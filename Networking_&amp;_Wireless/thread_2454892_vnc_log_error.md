---
title: "vnc log error"
date: 2020-12-08
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2020-12-08
I have gotten all our library computers fixed after upgrade to 20.04 which totally hosed vnc and rdp. Rdp still never works but the last computer won't go to vnc and when I check the logs in /home/darcy/.vnc I get this error 
Unrecognized option: -storepasswd

also another log say it keeps going to a progression of ports" 5900, 5901, 5902 etc. I am going through a wan router so always need to go to port 5900 which I thought I has fixed by putting the options in /lib/systemd/system/x11vnc.service and also putting there passwd 

```
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth -guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared

[Install]
WantedBy=multi-user.target
```

---

