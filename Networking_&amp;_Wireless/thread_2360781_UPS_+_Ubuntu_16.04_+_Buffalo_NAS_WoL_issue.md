---
title: "UPS + Ubuntu 16.04 + Buffalo NAS WoL issue"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by sidcypher-b on 2017-05-08
So I finally got around to getting a replacement battery for my APC UPS, previously however I did not have a NAS at that time.  The NAS supports WoL, through the "Auto" mode of the switch, and it has to keep getting packets every so often or it will shut back down after about 5min. 

The Ubuntu server runs 24/7 short of a power outage.. So on boot up I would like it to start the NAS up (which I also run 24/7) and keep it up until the UPS tells the server to shutdown, thereby stopping the WoL packets from being sent and shutting down the NAS a few minutes later.

I did find this post [https://ubuntuforums.org/showthread.php?t=1410353](https://ubuntuforums.org/showthread.php?t=1410353)

However in 16.04 it doesn't work I suppose because it doesn't use the old init.d stuff and has to have it as a systemctl service, and I have it chmod +x and it appears to work, however it doesn't drop back to a prompt afterwards.. I do not know if it is the shell script from that old post, or if it is related to the service I created shown below.

located in /etc/systemd/system/ wakenas.service

```
[Unit]
Description=NAS Stay Awake
After=network.target

[Service]
User=root
Restart=always
Type=notify
ExecStart=/usr/bin/wol.sh

[Install]
WantedBy=multi-user.target

```

wol.sh located in /usr/bin/  (MAC replaced with 0's)

```
#!/bin/sh

while true; do
        wakeonlan -i 192.168.1.215 00:00:00:00:00:00
        sleep 60
done


```

---

