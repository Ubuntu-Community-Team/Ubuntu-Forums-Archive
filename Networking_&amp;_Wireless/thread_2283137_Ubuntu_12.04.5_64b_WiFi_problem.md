---
title: "Ubuntu 12.04.5 64b WiFi problem"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by Dan_Rau on 2015-06-19
Hello
First of all thank you for this great OS that is -> Ubuntu :)
Then please excuse me if this issue has been already solved - it's my fault that didn't know about it - just show me the link and that's it :)

If not (if the problem is new) please have a look: 

I have an HP 650 laptop (brought 2 years ago) which it already came with Ubuntu 12.04.5 LTS 64b installed on it.
After sometime I start having problem with my WiFi connection: every time I do updates on my Ubuntu and the it asked me to restart my WiFi doesn't work at all -> it's like being disabled (the light is green from my F12 key - as the WiFi is OK - but I don't see any WiFi connections).
Here is my wireless controller (lspci | grep Network):
02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
So after updates and restart I have to do the steps (described in this link - see that)

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

and after another restart I see WiFi connections - and can connect to the one that it's mine and everything is fine.


OK. About 2 months ago I brought another laptop (ASUS ROG G751JM-T7043D, i7 3.5GHz, 17.3"FullHD,16GB,256GB SSD, nVIDIA GeForce GTX 860M 2GB GDDR5) which came with Free Dos, and so having already some experience with Ubuntu - I said why not, let's put Ubuntu on it: so I had installed Ubuntu 12.04.5 LTS on 64b.
I do updates every time it asks me to. So this is it -> after all the updates and restarts (the Asus laptop with Ubuntu - actually which it has the same version as the one from my HP) the new laptop doesn't have ANY problems with the WiFi. None! Everything is OK after updates and restarts - all the WiFi connections are there - without doing anything!


So I want to know what did I do wrong?
Why when I work with the same Ubuntu version (12.04.5 LTS on 64b), on HP I have to do some workaround to get WiFi connection and on Asus everything is normal?!

Thanks! ;)

---

### Post by howefield on 2015-06-19
Thread moved to the "*Wireless & Networking*" forum.

---

### Post by NoWayWin8 on 2015-06-19
> **Dan_Rau said:**
> Hello First of all thank you for this great OS that is -> Ubuntu :) Then please excuse me if this issue has been already solved - it's my fault that didn't know about it - just show me the link and that's it :) Sure, here ya go :) [http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

---

### Post by Dan_Rau on 2015-06-21
Thanks

---

### Post by wildmanne39 on 2015-06-21
On the computer with the 3290 wireless chip that driver is compiled from source which means it needs reinstalled every time the kernel is updated. If you install it using dkms then it will automatically reinstall itself when there is a kernel update and you will not have to do it manually any more. You first need to remove the old driver then do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential 
```
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/18/16/5561332-angepasster_DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
tar xvf 5561332-angepasster_DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
cd DPO_RT3290_LinuxSTA_V2600_20120508/
sudo make
sudo make install
sudo cp DPO_RT3290_LinuxSTA_V2600_20120508/common/rt3290.bin /lib/firmware 
```
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
You should already have the rt2800pci driver blacklisted but if not run the blacklist command above.
Driver courtesy of praseodym.

---

### Post by Dan_Rau on 2015-07-08
No!
It is happening again with the HP laptop!
I did some updates. It asked me for restart - and after restart the same thing -> WiFi not working
So I have to do that workaround again

---

### Post by praseodym on 2015-07-08
Yes, the driver needs to be recompiled after a kernel upgrade:
```

cd DPO_RT3290_LinuxSTA_V2600_20120508/
sudo make clean
sudo make
sudo make install
```

Alternatively, install the driver via dkms:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

