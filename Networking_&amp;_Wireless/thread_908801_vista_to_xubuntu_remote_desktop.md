---
title: "vista to xubuntu remote desktop"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by civ/crx on 2008-09-02
i would like to connect to a pc with xubuntu on it 

with a pc with vista using remote desktop 
thanks

---

### Post by civ/crx on 2008-09-02
bump

---

### Post by civ/crx on 2008-09-03
bump2

over lan

---

### Post by civ/crx on 2008-09-04
bump 6 pages down in 24 hours

---

### Post by civ/crx on 2008-09-08
bump

---

### Post by roadrun777 on 2008-09-08
You will find that your request is not an easy one.
There are several ways to do this, and most of them require some experience doing it a few times.

There are several issues here. 

How are these two machines connected to the internet? 

Are you running firewalls on any of the computers or routers between you and the device you want to connect to?

Do you need an encrypted connection between the two computers (advisable if your connecting over a public network)?

------------

It generally works like this:
You set your router to port forward a port of your choosing to your computer behind the router. You also set up a static IP, either via dhcp or just manually editing the scripts on the linux pc.

Then you need to figure out how to get VNC server running on your linux box probably binded to a local address only, like 127.0.0.1:5900. Then you have to set up SSH. Then you have to create your own certificates for SSH. Then you have to set the incoming SSH connection up in your routing tables/firewall so that it has access to the loop-back (127.0.0.1). Then on the xp computer you have to install puTTy and the certificates for ssh.
Then you have to figure out how to force VNC to pipe it's connection through puTTy on the win* machine, which is something I have no idea how to do.

There are probably some step by step tutorials on how to do this somewhere. At least you have the keywords on what to search for now. I know there are people working on GUI front ends to do all this but I don't know who, and whether their projects are in a testing or completed phase. I noticed on one of the new live-cd's there was an option for VNC server, so it may have a GUI configuration panel now. Which, at least, makes one of the steps a little easier.

---

