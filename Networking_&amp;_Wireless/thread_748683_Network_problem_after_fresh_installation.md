---
title: "Network problem after fresh installation"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by vazir on 2008-04-07
Hi Folks,

I am new :confused: to Linux. I bought a new HP PC (a6400f E2200) and installed Ubuntu 7.10 Desktop version on the machine. Installation went pretty smooth. After login, the Ethernet network is not coming up. There is no wireless card for this computer. I have tried System/Administration/Network menu to configure DHCP, it did not work. I tried Static IP, still it is not able to talk to the network. 

The /etc/networks/interfaces file is as follows:
/***************************
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.65
netmask 255.255.0.0
gateway 192.168.1 254


auto eth0

/***************************
 
I would appreciate if you can provide some help to get the linux platform on the network.

Thanks,
  Vazir

---

### Post by superprash2003 on 2008-04-08
please post results of ifconfig

---

### Post by alguin2 on 2008-05-27
See the fix by AgDon92 / seriftr / jhwilliams:

**_Thread:_** [http://ubuntuforums.org/showthread.php?t=799662]("http://ubuntuforums.org/showthread.php?t=799662") 

[B][U]...More specifically, the below postings: 
[/U][/B][http://ubuntuforums.org/showpost.php?p=5002506]("http://ubuntuforums.org/showpost.php?p=5002506")
[http://ubuntuforums.org/showpost.php?p=5017262]("http://ubuntuforums.org/showpost.php?p=5017262")

---

