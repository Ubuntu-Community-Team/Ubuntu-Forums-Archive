---
title: "no idea how to use ssh, please help"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by mjpolifka on 2007-09-22
This is probably in a lot of places, but I've been searching for a few days now and either I can't find it, or I already have and I have no idea what is being said.  I don't know anything about networking, I'm trying to learn right now, but I want to use ssh or telnet to remotely admin my server (at least as much as is possible).  I tried "telnet 192.168.1.108" and it says port 23 is refused and i tried "ssh 192.168.108" and it says port 22 is refused.  I used nmap and only port 21 and 80 seem to be open.  So I tried "ssh -p 80 192.168.1.108" and it doesn't do anything, just went to a new line and seemed to hang until I hit ctrl-c.  I don't even know what ssh does, can someone please explain how to do this without getting to technical?  Thanks.

---

### Post by noob12 on 2007-09-22
OK.  The server side of ssh isn't installed on Ubuntu desktop by default.

You need to install it first.
```

sudo aptitude install openssh-server

```

If you are running a firewall make sure port 22 is open to new TCP connections inbound.

---

### Post by phillips321 on 2007-09-22
instakll the ssh server on the server as mentioned above

then from the client box (i guess the one u want to connect to it from) run the command 
```
ssh 192.168.1.108
```
any mor probs come back and we'll help

p.s. i hope u realise that ssh only shows a terminal window, there are no "graphics", if u wish for graphics u must install something like vnc

---

### Post by mjpolifka on 2007-09-23
Thank you, that worked great.  And yes, I realize no graphics; I'm running debian on my server with no x (it's an old toshiba tecra laptop that I got for free, and with debian it works great despite almost no system resources).  Thanks again.

---

