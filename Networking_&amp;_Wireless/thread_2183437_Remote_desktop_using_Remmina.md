---
title: "Remote desktop using Remmina"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Michael_Kearney on 2013-10-24
I'm trying to remote access my home server on the network, using Remmina and SSH tunnel. Connecting Ubuntu 13.10 (client) to Lubuntu 13.10 (server).

I have it setup and can connect through terminal using SSH. When I go to connec with remmina it just says "connecting to 192.x.x.x through SSH tunnel" and it just sits there.

What do I need to do to have it connect? I'm not sure I have Remmina set up right.

The user name and password on the "basic" tab, is that the username and password for the server? I have it set to VNC, and on the SSH tab selected "ssh tunnel", same server at port 22, and put in the username there and selected "password"

What else can I check to get this working?

---

### Post by Michael_Kearney on 2013-10-25
bump

---

### Post by steeldriver on 2013-10-25
IIRC you need to check the 'Tunnel via loopback address' box in the SSH tab as well

Also you will need to append the port number or display number to the server hostname if you are using a non-default port

Obviously there must be a VNC server listening on the other end ;)

---

### Post by Michael_Kearney on 2013-10-25
I checked the "tunnel via loopback address box" and still no luck. server should be running, and I can connect through terminal, so it must be right? how can I check and make sure? also, is there a way to find the display number of the server? from time to time I will get the  "cannot open display" error running other programs through terminal.

---

### Post by steeldriver on 2013-10-25
On the Lubuntu box, you could look at the likely ports

```
sudo netstat -nlp | grep ':59..'
```

What VNC server are you using? regular Ubuntu uses vino, I don't know whether Lubuntu ships with a default 'desktop sharing' server or if you need to install vino or x11vnc?

---

### Post by Michael_Kearney on 2013-10-25
I have vino installed.

---

