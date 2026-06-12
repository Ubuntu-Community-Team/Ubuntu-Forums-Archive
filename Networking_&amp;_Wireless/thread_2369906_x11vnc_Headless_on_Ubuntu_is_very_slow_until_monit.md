---
title: "x11vnc Headless on Ubuntu is very slow until monitor connected"
date: 2017-08-28
forum: Networking &amp; Wireless
---

### Post by eddy555 on 2017-08-28
I'm running x11vnc on Ubuntu as a service at startup. It generally works fine, but I want to run it headless. If I start the server with a monitor connected but off, VNC connects and responds quickly, however if I restart the server without a monitor connected (I want to remove the monitor from my desk) then it's painfully slow to use - like 5 fps response, until I connect a monitor again and then it's fine.


Here's the content of my service file


```
[Unit]
Description=Start x11vnc at startup
After=multi-user.target


[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -display :0 -geometry 1024x768 -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared -o /var/log/x11vnc.log


[Install]
WantedBy=multi-user.target

```I'd be really grateful if someone can point out where I've gone wrong with this. Thanks

---

### Post by wildmanne39 on 2018-07-17
Old thread closed. Hello mangocats, I am moving your post to its own thread in the server sub-forum located here:

[https://ubuntuforums.org/showthread.php?t=2396546](https://ubuntuforums.org/showthread.php?t=2396546)

---

