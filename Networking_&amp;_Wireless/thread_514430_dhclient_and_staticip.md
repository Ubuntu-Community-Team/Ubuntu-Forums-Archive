---
title: "dhclient and staticip"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by gishaust on 2007-07-31
Hi everyone

There will  be a simple answer but as I am a newbie I don't know where to look,

when I set my unbuntu server I gave everything on the network static ip (because i did not know about dhcp) now I have moved up to dhcp and I want the Ubuntu server to become a client. I can cat etc/network/interfaces and I get the static ip 192.168.1.2. can some one please tell me where I can remove this  so that I don't have to type in dhclient eth0 all  the time.

Gishaust

---

### Post by punx45 on 2007-07-31
turn off network interfaces:
```
sudo ifdown eth0
```

back up /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

edit /etc/network/interfaces:
```
sudo nano /etc/network/interfaces
```

take out the lines that refer to the static IP: which will look similar to this:
```
iface eth0 inet static
             address 192.168.0.111
             netmask 255.255.255.0
             gateway 192.168.0.1
```

replace with 
```
iface eth0 inet dhcp
```
save.

bring interfaces back up:
```
sudo ifup eth0
```

assuming you have a DHCP server running somewhere (such as a router) that shoud do it.

EDIT!:
you may also ignore the ifdown and ifup instructions, and simply restart at the end by doing:
```
sudo /etc/init.d/networking restart
```


but, are you sure you want the IP of the system to be DHCP?   you said it was a server, and you want a server to have a static IP so that it can always be found.

---

### Post by gishaust on 2007-07-31
That is what I was looking for thank you very much

---

