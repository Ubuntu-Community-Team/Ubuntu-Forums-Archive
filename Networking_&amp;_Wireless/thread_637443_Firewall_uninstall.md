---
title: "Firewall uninstall"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by syborfical on 2007-12-11
The other day I downloaded updates for ubuntu.
 I am running 7.04, it install firestarter and some other crap. 

Now I can&#8217;t surf the web and its really annoying me.

Is there a way to remove the firewall / the programs that are blocking the internet? 
And just get my ubuntu box back on the net ?

---

### Post by ruibernardo on 2007-12-11
Hi syborfical,

```
sudo apt-get remove --purge firestarter
```
Will remove firestarter and its configuration files. Reboot to clear all iptables settings.

The next time you install firestarter, it will be without any previous definitions, like the first time you installed it.

Before you try a new firewall, always remove any firewall you have installed and reboot. Then install the next one.

---

### Post by Emerzen on 2007-12-11
It's unlikely that Firestarter is blocking you from surfing the web as it set iptables to permissive for outgoing connections.  On the other hand, if it Firestarter, then removing it should clear the problem.

---

### Post by syborfical on 2007-12-11
I've all ready removed iptables and firestarter and i still cant access the internet... 

is there anyway to fix this or anything i need to delete?

---

### Post by ruibernardo on 2007-12-11
> **syborfical said:**
> I've all ready **removed iptables** and firestarter and i still cant access the internet...Don't remove iptables! Reinstall it again with:
```
sudo apt-get install iptables ubuntu-standard
```Reboot and verify if you don't have any firewall installed that is changing iptables. Type:
```
sudo iptables -L
```It should output something like:
```
Chain INPUT (policy ACCEPT)
target      prot opt source            destination

Chain FORWARD (policy ACCEPT)
target      prot opt source            destination

Chain OUTPUT (policy ACCEPT)
target      prot opt source            destination
```If it shows more things, you still have some firewall installed. If it is clear as shown above, the problem is not related to iptables or firewall.

---

### Post by syborfical on 2007-12-11
I&#8217;ve already uninstalled ip tables and firestarter,

I still have no access to the internet. So I cant use apt-get I cant get on the internet or ping any internet addresses.

I did notice last night I cant ping my router 192.168.1.1 which is a link sys AG310.
I am getting DHCP and all my dns server addresses are correct.
I can ping all computers on the local network.
I can not ping the router or anything on the other side of the router.

Is this a firewall or router issue? I have 90% of ubuntu 7.10 torrent downloaded I only want to get my Ubuntu box back on the net so that can complete so I can format and fresh install.

---

### Post by ruibernardo on 2007-12-11
If you still have your CD (alternate or desktop), you can install "iptables" and "ubuntu-standard" back and all the packages that are there.

Go to the menu System > Administration > Software Sources. Uncheck the internet repositories (main, restricted, universe and multiverse). Check the CD-ROM below. On the "Third party" tab uncheck the internet repositories too. Click "Close" and reload.

Now you should be able to reinstall "iptables" and "ubuntu-standard" and verify.

---

