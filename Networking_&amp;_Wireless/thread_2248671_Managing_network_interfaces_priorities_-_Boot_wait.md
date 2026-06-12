---
title: "Managing network interfaces priorities - Boot waiting for network config."
date: 2014-10-16
forum: Networking &amp; Wireless
---

### Post by thiago-canaes on 2014-10-16
Hello!
I have a notebook that I use to access a Wireless and a Wired network at the same time.
I use the Wireless as main, and use the wired to bridge my vmware.

I made it work by editing the /etc/network/interface file. But now, the system wont boot until the network is configured. 
At work, its not a big issue, since I do have a wired connection. But, at home where I have only Wifi, it just hangs for a long time. And even after it logs into system, takes to long to Wireless connect. Looks like it keeps looking for a wired connection after loging, and wont bother searching for wireless connection.

Here is my /etc/network/interface:

> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
  metric 10


Tnks in advance,
TC.

---

### Post by ian-weisser on 2014-10-16
[EDIT] Retracted. I just realized my solution likely wouldn't work.

---

### Post by thiago-canaes on 2014-10-16
I was able to remove the boot time by editing /etc/init/failsafe.conf.
Found the answer here: [http://askubuntu.com/questions/213614/waiting-for-network-configuration-problem](http://askubuntu.com/questions/213614/waiting-for-network-configuration-problem)

But I still fill there sould be something I could do on /etc/network/interface to fix it, instead of messing with other files...

Ubuntu now boots faster, but still taking to long to connect to Wifi. Almost 5 minutes after system login...

I tried adding these lines to the file, but it didnt work..
auto wlan
iface wlan0 inet dhcp

---

