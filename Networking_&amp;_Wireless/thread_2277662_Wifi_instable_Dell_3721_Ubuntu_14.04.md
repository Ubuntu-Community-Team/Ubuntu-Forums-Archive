---
title: "Wifi instable Dell 3721 Ubuntu 14.04"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by sebastian23 on 2015-05-10
Hi. I use Ubuntu 14.04. My Wifi connection is very instable. Sometimes it works a whole day, but most of the time I have to reboot my notebook (Dell 3721) couple of times a day. Wifi connection just disappear and then it try to automatically reconnect, most of the time without success. Even connection is established it's often very slow while other deviced works fine in my home network.

In the past, before I upgraded my system from 13.04 to 14.04, I used this command to install a special wifi driver:

sudo apt-get install --reinstall linux-headers-generic build-essential dkms bcmwl-kernel-source
echo -e "blacklist b43\nblacklist ssb\nblacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
May this driver doesn't fit to 14.04? Is there a new one which could work?
This is a old thread of me (with a differnt username) which may could help to find a solution: [http://ubuntuforums.org/showthread.php?t=2148813](http://ubuntuforums.org/showthread.php?t=2148813)

---

### Post by sebastian23 on 2015-05-12
Help me, please. Now I have to use a wired connection, wifi is to unreliable with this computer.

---

### Post by Pilot6 on 2015-05-12
Please give output of

lspci -knn | grep Net -A2

---

### Post by sebastian23 on 2015-05-12
Here it is:

> seb@Notebook:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl


---

### Post by Francesco_Verlato on 2015-05-12
I have the same problem on 15.04...

---

### Post by Vladlenin5000 on 2015-05-13
Read Special Case #2: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by sebastian23 on 2015-05-19
I deleted bcmwl-kernel-source and installed it again. It's more stable, but connection still disappear sometimes.

---

### Post by Francesco_Verlato on 2015-05-25
I had to use the ethernet cable because it has become impossible:confused:

---

### Post by sebastian23 on 2015-05-26
Nobody can help, please?

---

