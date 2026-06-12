---
title: "dont have network connection"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by 007casper on 2008-11-24
fresh installation of ubuntu 8.10 64bit...

I followed the instructions on
[http://howtoforge.com/perfect-server-ubuntu-8.10-p2](http://howtoforge.com/perfect-server-ubuntu-8.10-p2)

and network connection didnt work.  I have tested the cable on my laptop.  And it works.  Plug it back to the server... test it again it still doesnt work.

since I dont have connection I cant continue with the set up.  I guess I could use aptoncd [http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)... 

however I would like to set it through online connection.

in the terminal ifconfig
```
eth0 Link encap:Ethernet HWaddr 00:1f:c6:d5:b9:90
     inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
     UP BROADCAST MUTLICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
     Memory:fdfa0000-fdfc0000

lo Link encap:Local Loopback 
   inet addr:127.0.0.1 Mask:255.0.0.0
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:4 errors:0 dropped:0 overruns:0 frame:0
   TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0
   RX bytes:382 (382.0 B) TX bytes:382 (382.0 B)
```

please, help thank you.

007casper

---

### Post by 007casper on 2008-11-24
Since I couldnt get connection through instructions from here [http://howtoforge.com/perfect-server-ubuntu-8.10-p3](http://howtoforge.com/perfect-server-ubuntu-8.10-p3)

I tried other settings

in the terminal vi /etc/network/interfaces

```
#This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces (5)
#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.102
        netmask 255.255.255.0
        gateway 192.168.1.1
```

on the server I have four ethernet ports... they are as follows
LAN 1/2(RJ-45)ports
LAN 3/4(RF-45)ports
eth0, eth1, eth2, eth3 

I have only one cat6 cable attached to one of the ports.  After looking at the motherboard manual I believe I plugged it to LAN 1...

on the terminal vi etc/resolv.conf I wrote
nameserver 192.168.1.1

I really appreciate any help I can get... thank you

---

### Post by 007casper on 2008-11-24
bump :-(

---

### Post by Olivier2371 on 2008-11-24
Hi there,

Which Ubuntu 8.10 64bit? (server version or the normal version)

Are you trying to connect to the internet or to create a local network with other computer?

The first link you posted talk about setting up a server.

The second link talk about setting up the perfect server.

---

### Post by Iowan on 2008-11-24
The DHCP *should* work.  It's possible the NIC deeds a different driver.  For static address, you may need to try [this]("http://ubuntuforums.org/showthread.php?t=974382") NM but workaround.

---

### Post by 007casper on 2008-11-25
I am setting up Ubuntu 8.10 64bit server version.  I found the second link through a thread that someone had a similar problem on 8.10 and it was suggested that he uses aptoncd which didnt solve the problem 

I guess there is a bug in regards to network manager

I am going to try the link Iowan suggested... I will post an update

Thank you guys.

---

### Post by 007casper on 2008-11-29
I did a clean install and it acts like it is going to connect to online and then it fails to apt-get update or apt-get upgrade... checked the link Iowan provided... no luck

I tried to ping google.com... it failed

It gives me "W: failed to connect".  The motherboard manual has lan driver instructions.  I was wondering if I should download Contents-amd64.gz from [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/) and 
[http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/) to a dvd and unpack it from there. 

is there anything else I need to burn for a full update?

Then, I figured I will install the driver from the motherboard disk.

any suggestions

---

### Post by 007casper on 2008-11-30
works like charm... after pulling my hair a few times... got it working 

thank u everyone
-
I wish there was instructions on apt update without internet connections.

---

