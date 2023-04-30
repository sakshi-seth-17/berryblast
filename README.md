# berryblast
It is a Blast+ server which enables to run BLAST analyses in the cloud and provides a graphical interface for easy configuration and access management. The port 4567 is open to public and berryblast is hosted on it so it can be accessed without vpn.

---

# Ref:
https://sequenceserver.com/

---

### Steps to install 
1. `sudo gem install sequenceserver` 
2. Clone this repository inside /var/www/aspendb/probesearch. \
`git clone https://github.com/sakshi-seth-17/berryblast.git`
3. To start the service run – `sequenceserver` 
4. To access any API from outside the server, the API needs to be listed on the server.
  - `sudo ufw allow 4567`
  - `sudo ufw enable`
  - `sudo ufw status`
5. Browse - http://aspendb.uga.edu/probesearch/berryblast/


### Create service file to make the app run indefinitely
`sudo nano /lib/systemd/system/sequenceblast.service` \
Paste below lines inside the file by making necessary changes


              [Unit] 
              Description=Sequence Blast 
              After=multi-user.target 

              [Service] 
              User=webserver 
              Type=idle 
              ExecStart=sequenceserver -p 4567
              Restart=always


              [Install] 
              WantedBy=multi-user.target 

`sudo chmod 644 /lib/systemd/system/sequenceblast.service` \
`sudo systemctl enable sequenceblast.service` \
`sudo systemctl daemon-reload` \
`sudo systemctl start sequenceblast.service` \
`sudo systemctl status sequenceblast.service` 




---
### Location details of the components:
1.	Application code path (on webserver - webserver@128.192.158.63) path: /var/www/aspendb/probesearch/berryblast

---
### Folder Structure
- index.html
