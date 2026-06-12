---
title: "Network config using /etc/network/interfaces"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by DFHansen on 2009-12-11
I tried configuring a static IP using the file /etc/network/interfaces, and could not get it to work, but finally figured out what I was doing wrong with the graphical network interface (System...Preferences...Network Connections), so I got the network up and running.  My question is that the the file and the graphical interface don't seem to work in conjuction with each other.  What I was expecting was if I made a change to one, it would show up in the user interface, and vice versa.  Am I editing the correct file.  Everything I read on the web says that I am.   

Here is my /etc/network/interface file:

#loopback
   auto lo
   iface lo inet loopback

#eth0 setup
   iface eth0
   address  xxx.xx.xxx.xx
   netmask  255.255.255.0
   gateway  xxx.xx.xxx.1

I also tried editing the second line 
   auto lo eth0
to get eth0 to automatically activate on booting.  I then tried deleting any reference to eth0 in the graphical interface to see if I could get it to read the interfaces file.  I was able to get the network up by running ifup eth0 after booting, but could not get it to automatically start up.  In 9.1 is the /etc/network/interfaces file still used?

---

### Post by jbrown96 on 2009-12-11
It would be much easier to configure this in NetworkManager. NetworkManager is probably overriding/conflicting with any settings you make.

1) Undo what you have done/
2) Right click on your network icon by the clock-->edit connections-->edit "auto eth0"-->IPv4 settings-->Manual, then fill in your info.

---

### Post by M!K3_$ on 2009-12-11
after you make changes to the interfaces file do this...
```
sudo /etc/init.d/networking restart
```
(may be a little off, that's from memory)

---

### Post by cherva on 2009-12-11
For eth0 it should be like this:
```

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

```

---

### Post by M!K3_$ on 2009-12-11
> **cherva said:**
> For eth0 it should be like this:
```

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

```

right, i never even checked his syntax. there's your problem.

---

### Post by cherva on 2009-12-13
DFHansen, if your problem is solved please mark the thread as solved :)

---

### Post by Iowan on 2009-12-13
> **cherva said:**
> ... please mark the thread as solved(That'd be under Thread Tools - Thanks!)

---

