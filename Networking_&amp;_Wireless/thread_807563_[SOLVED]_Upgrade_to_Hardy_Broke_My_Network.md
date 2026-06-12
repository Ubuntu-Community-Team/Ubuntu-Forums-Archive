---
title: "[SOLVED] Upgrade to Hardy Broke My Network"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2008-05-25
I recently upgraded from Feisty (7.10) to Hardy (8.04) and it broke my networking :(
I posted in the Absolute Beginners forum here: [http://ubuntuforums.org/showthread.php?t=807020](http://ubuntuforums.org/showthread.php?t=807020)

but I seem to have hit a road block on it (as far as support goes)...
Basically what it boils down to is each time I reboot I have to change the last three lines of **/etc/network/interfaces** to/from:
```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#    bridge_ports eth1
iface eth1 inet dhcp
```
or
```
auto lo
iface lo inet loopback
auto br0
iface br0 inet dhcp
    bridge_ports eth1
#iface eth1 inet dhcp
```
and issue **sudo /etc/init.d/networking restart**...
-=-
So to re-iterate if the last three lines are:```
iface br0 inet dhcp
    bridge_ports eth1
#iface eth1 inet dhcp
``` 
Upon reboot I have to change it to:```
#iface br0 inet dhcp
#    bridge_ports eth1
iface eth1 inet dhcp
```
and issue **sudo /etc/init.d/networking restart**
And vice versa EVERY SINGLE TIME I REBOOT the machine, just to get the network working again :confused:

Can someone help me figure this out?
Thanks in advance,
-BassKozz

---

### Post by copperpot on 2008-05-26
Hello,

I am having the same problem that you have. I did not check yet the file yet to see if I have the same problem, but I was reading in your other post and noticed that I have also installed Virtualbox and VMWare server. Though, I can not recall if that issue generated after I installed any of them or when.
Also, what I noticed is that if I completely shutdown the computer, and then I power it on, the network works fine.

Any ideas of what could be going one here? Somebody could please help?

---

### Post by BassKozz on 2008-05-26
> **copperpot said:**
> 
Also, what I noticed is that if I completely shutdown the computer, and then I power it on, the network works fine.
My problem persists even if I completely shutdown and power back on. :(
I wish it was only on restart, then I could live with it, but right now if I shutdown and I power on remotely ([WOL]("http://en.wikipedia.org/wiki/Wake-on-LAN")) I can't connect to it remotely :(

---

### Post by BassKozz on 2008-05-26
Solution Found: [http://ubuntuforums.org/showpost.php?p=5046957&postcount=21](http://ubuntuforums.org/showpost.php?p=5046957&postcount=21)

---

### Post by copperpot on 2008-05-26
I will check that reply when I log into Ubuntu... hopes that works, as it is very frustating not being able to have the network working everytime.
Thanks for the info!
I'll keep you posted.

---

### Post by BassKozz on 2008-05-26
> **copperpot said:**
> I will check that reply when I log into Ubuntu... hopes that works, as it is very frustating not being able to have the network working everytime.
Thanks for the info!
I'll keep you posted.Did it work for you copperpot?

---

