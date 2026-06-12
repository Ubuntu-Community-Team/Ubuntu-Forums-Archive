---
title: "Problems with 8.10, WIFI and 3945abg intel"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by mee.six on 2008-11-11
Hi, everyone

Just updated to 8.10, and simply can't find my local WiFi-network, even when I enter network ID, I'm getting "Network disconnected" message in result :( is there any way to fix it?

thanks in advance,
mee

---

### Post by joehill on 2008-11-11
I've got the same problem today.  I upgraded to Intrepid several weeks ago, then after today's kernel upgrade my wireless is completely broken.  I haven't had any wireless problems over the past couple years, then today it stopped working completely.  Seems like these updates weren't fully tested.

Any ideas on how to diagnose the problem?  I tried booting with the previous kernel but that doesn't help.  This is not good!

---

### Post by tvtech on 2008-11-11
you might want to check these links

[https://launchpad.net/ipw3945](https://launchpad.net/ipw3945)

there were a number of issues with the intel pro/wireless 3945, up to and including a kernal bug that would totally disable it reflash it and turn it into a brick.  they fixed that or so they said.  that was from alpha 5 I believe.    

check out launchpad though, seems like a TON of mentions for problems with this connection. [http://launchpad.net](http://launchpad.net)

my own wireless woes are with a intel 5100 abgn for some reason networkmanager doesn't like to manage it after the kernal boots, and I have to manually reinitialize it every time I want to use it.   pain in the butt if you ask me.

---

### Post by mee.six on 2008-11-11
well, I have this problem out of a box, actually.

thanks, checking links...

---

### Post by redfox7691 on 2008-11-12
On my Compaq nc8430 (lspci report 3945ABG [Golan] Network Connection rev 02): with Ubuntu 7.10 (32 bit) my wifi connection was all functional, now with 8.10 64bit some network are not reachable.
This behavior is not joined with access point brand: in this moment I'm in a large wifi network (with some essid) and at 2nd floor it works, at 1st floor it doesn't work. My home wifi works fine.

---

### Post by mee.six on 2008-11-12
My AP is D-Link, but no APs here available, so I can't tell you about other brands.

So, after trying about 5 different targets for make, it appeared that I've to install ieee80211, because mine isn't correct version of ieee80211. So, I'm having this, while installing ieee:
```
root@mee-laptop:~/ieee80211-1.2.18# make SHELL=/bin/bash
Checking in /lib/modules/2.6.27-7-generic for ieee80211 components...
make -C /lib/modules/2.6.27-7-generic/build M=/root/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /root/ieee80211-1.2.18/ieee80211_module.o
/root/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/root/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/root/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/root/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/root/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/root/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/root/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/root/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2



```

---

### Post by mee.six on 2008-11-13
Updated system, even new kernel was downloaded, but no changes, still doesn't work :(

---

### Post by puppy on 2008-11-13
I'm having the same problem - after a recent kernel upgrade in 8.10 I no longer have my wireless connection listed using iwconfig - it's gone altogether. I just wish a dev would admit there's a problem...

---

### Post by davidjmaxey on 2008-12-01
I am having the same issue when I upgraded to the newest kernal for 8.10 my Athero wifi just wont see my wireless network!

---

### Post by stevejohnson on 2008-12-01
I dont know the where the problem has occured. I have serious issues over the WIFI network and also with my local host provider. Try to resolve my issue as soon as possible. 
=============================
steve
[medical transcription](http://stevetranscription.wordpress.com)

---

### Post by mnoutside on 2008-12-01
I new to this, but is there a way to go back to an older version?
My wireless worked great until I did the upgrade to 8.*

---

### Post by panagath on 2008-12-09
I have the same problem. Using ubuntu 8.10 , wireless was working fine [intel 3945] until I got the big pack of updates ubuntu was suggesting. Since then although in ifconfig -a    I can see the wlan0  , I can enable it. PLEASE HELP...

---

### Post by kgas on 2008-12-09
I have noticed that many with intel 3945 ABG wireless got problem. But in my case Ubuntu 8.10 was fine with Lenovo 3000 N100 out of box. Arch Linux got problem with this and Arch has a nice wiki to solve most of the problem. You can see Arch wiki to find a solution.

[http://wiki.archlinux.org/index.php/Wireless_Setup](http://wiki.archlinux.org/index.php/Wireless_Setup)  

Hope this may help you.

---

### Post by panagath on 2008-12-09
actually wireless was working OK with the original installation of ubuntu. When I installed the updates it stopped working.

---

