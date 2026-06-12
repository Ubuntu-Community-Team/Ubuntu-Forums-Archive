---
title: "Wired Connection No Worky"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by pseudosig on 2008-04-30
Okay, I'm new to networking on linux and I'm having some serious issues trying to get my wired connection to work.  I upgraded from Ubuntu 7.10 to Ubuntu 8.04 via the update manager.  My wired connection on eth0 worked with 7.10... and now it doesn't with 8.04.  I'm nearly certain that my static ip info is correct, because if I boot up 8.04 with the old linux kernel (2.6.22-14-generic), my wired connection works fine.  If I boot up 8.04 with the new linux kernel (2.6.24-16-generic), my wired connection doesn't work.  Same settings in terms of /etc/network/interfaces and /etc/resolve.conf etc.  So is the new kernel loading a module that conflicts with my old settings or something... I've tried everything, except that what works.  ANY help would be great.

Thanks in advance...

---

### Post by pseudosig on 2008-04-30
If this helps also, if I type ifconfig in either either kernel, I get the same setup info for eth0.

---

### Post by pseudosig on 2008-04-30
No one have any ideas on this?

---

### Post by al-fil on 2008-05-01
I have similar issues: Updated from 7.10 to 8.04 a couple days ago and my wired (my only connection for my desktop pc) doesn't work anymore. When I first installed 7.10 I had no connectivity problems of any kind. So far I've only been able to get a connection if I call these commands on terminal:
```
sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0
sudo /etc/init.d/networking restart 
```
Problem is I have to do this every time I reboot. User sam_delta (who's way more experienced than I am) is trying to help me find a way to add these commands to start-up but so far we haven't made much progress. Anyway, check out this thread (post #57 onward):

[_"no internet in Ubuntu Hardy heron"_]("http://ubuntuforums.org/showthread.php?t=766800&page=6")

Please let us know if you find a solution. I'll do the same here:).

---

### Post by al-fil on 2008-05-01
OK, this seems to do it for now:

- Run gedit as root and open /etc/rc.local
- Atl+F2 -> gksu gedit /etc/rc.local
- Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

From: [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)

I'd recommend making a backup copy of *rc.local* before editing the file. Let me know if this works for you as well.

---

### Post by pseudosig on 2008-05-01
> **al-fil said:**
> OK, this seems to do it for now:

- Run gedit as root and open /etc/rc.local
- Atl+F2 -> gksu gedit /etc/rc.local
- Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

From: [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)

I'd recommend making a backup copy of *rc.local* before editing the file. Let me know if this works for you as well.

THANK YOU!!!  This works great.  Your help is much appreciated.

---

### Post by al-fil on 2008-05-01
Glad it worked for you too :)

---

