---
title: "vnc4server: No password configured for VNC Auth"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by fltrx on 2016-05-13
I want to use my Ubuntu Server 14.04.1 LTS as a VNC server. I installed lightdm and vnc4server. On the client, I installed xvnc4viewer. Whenever I try to connect to the server, after I typed in my password, I get:

> No password configured for VNC Auth

Here is my /etc/lightdm/lightdm.conf:

> [SeatDefaults]
autologin-user=
user-seesion=ubuntu
greeter-session=unity-greeter
allow-guest=false
[XDMCPServer]
enabled=true
port=177
[VNCServer]
enabled=true
command=/usr/bin/Xvnc4 -SecurityTypes None -rfbauth /etc/vncpasswd
listen-address=192.168.178.23
port=5900
width=1280
height=1024
depth=24

192.168.178.23 being the IP adress of my server.

To set the VNC password, I ran sudo vncpasswd /etc/vncpasswd. I had to run it as sudo to get write access.

What can I do to make it work?

---

### Post by slickymaster on 2016-05-13
*Thread moved to **Networking & Wireless**.*

---

### Post by fltrx on 2016-05-14
Nobody has any idea what to do about this?

---

### Post by fltrx on 2016-05-27
I solved this issue by upgrading the server to the next Ubuntu LTS version.

---

