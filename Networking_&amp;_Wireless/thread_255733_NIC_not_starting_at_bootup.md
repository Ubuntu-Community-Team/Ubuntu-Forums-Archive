---
title: "NIC not starting at bootup"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by Badchoices on 2006-09-11
Just installed 6.06 this morning - one reoccurring theme so far has been the NIC not starting on bootups. Once logged into the GUI, I need to open the network config and then deactivate and reactivate the card.  Once that is done everything comes right - just a bit annoying and as I'm testing this with the intention of replacing XP, I want to make sure the wife doesn't run into these issues.

Any advise would be helpful. - Cheers

---

### Post by linuxusr50 on 2006-09-11
Make sure you have the auto statement in the /etc/network/interfaces file.

It should look like this.

> auto lo ethxwhere "x" is the number of you ethernet adapter (i.e. eth0)

---

### Post by Badchoices on 2006-09-12
appears to be there

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

The possibility exists that I'm missing something here.

---

### Post by linuxusr50 on 2006-09-12
If you open a terminal and type in
```
sudo ifup -a
``` does the ethernet device come up?
If so then your interfaces file should be correct as
I believe the ifup command reads from the /etc/network/interfaces file.


Not that it will likely make a difference, but my interfaces file looks more like this.

> auto lo eth0 eth1 ath0 wlan0

iface lo inet loopback
iface eth0 inet dhcp
iface eth1 inet dhcp
iface eth2 inet dhcp
iface ath0 inet dhcp
iface wlan0 inet dhcp

---

### Post by jinx099 on 2006-09-12
check out this thread:

[http://ubuntuforums.org/showthread.php?t=193850](http://ubuntuforums.org/showthread.php?t=193850)

---

