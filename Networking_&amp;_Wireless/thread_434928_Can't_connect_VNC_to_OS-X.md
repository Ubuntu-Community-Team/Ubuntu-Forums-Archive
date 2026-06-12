---
title: "Can't connect VNC to OS-X"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Azyx on 2007-05-06
Hi
When i try fron my 7.04 Ubuntu to my OS-X 10.4 machine with TSclient and vnc I can't connect. I get "Unknown message type 255 from VNC server  ShmCleanup called"  and the connection closedown

---

### Post by dbott67 on 2007-05-06
[COLOR=Blue]*EDIT: I just tried using TSClient & it worked for me.*[/COLOR]

You can try using 'vncviewer':
```
vncviewer ip.address.of.osx
```If that fails, make sure the firewall on OSX is disabled or allows port 5900 and that VNC server is listening on port 5900:

```
MAC-OSX:~ dbott$ netstat | grep 5900
tcp4    0    0    192.168.1.108.5900    192.168.1.106.4233    ESTABLISHED
MAC-OSX:~ dbott$
```Here's a screenshot of VNC & OSX, and another one from a couple of years ago (Hoary@work connecting to my home OSX machine and a Win2K machine in a training lab at work).

-Dave

---

### Post by Azyx on 2007-05-07
I read that I would use tightvnc in stead of vnc and followed this guide:  

[https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop)

Now I get connection. I can move the mouse and use my keyboard on OS-X machine, but the OS-X desktop on my Ubuntu i black.

---

### Post by dbott67 on 2007-05-07
What kind of connection to the OSX computer do you have (LAN: 10/100 or WAN: dialup, DSL, cable)?

---

### Post by Azyx on 2007-05-07
It's my home-computers bihind a router and it's 100Mbit LAN. 


> **dbott67 said:**
> What kind of connection to the OSX computer do you have (LAN: 10/100 or WAN: dialup, DSL, cable)?

---

