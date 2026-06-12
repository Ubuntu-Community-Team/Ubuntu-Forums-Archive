---
title: "Question about which wifi driver I'm using?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by jacatone on 2009-03-08
I'm running Ubuntu 8.10. This version of Ubuntu has the Realtek 8187 wifi dongle driver but my wifi dongle takes the RTL 8187B driver, so I tried installing it's Win98 driver using ndiswrapper. What command would I use to determine if I'm using the ndiswrapper driver or the old 8187 one? If I'm using the old 8187 one, how do I make the change? Thanks.

---

### Post by unutbu on 2009-03-08
```
sudo lshw -C network
```

Near the bottom of the output, depending on your wireless adapter, you might see the driver that is being used. For example:

```
      configuration: broadcast=yes **driver=ndiswrapper+neta5agu** driverversion=1.53+D-Link,05/08/2006,1.5.202.2 ip=192.168.1.81 link=yes multicast=yes wireless=IEEE 802.11g
```

If your wireless adapter does not display the driver, then you could also run
```

lsmod | grep 8187
lsmod | grep ndiswrapper
```
To see which module is loaded in the kernel.

---

### Post by jacatone on 2009-03-08
These commands show the following:

jacatone@eMax ~ $ lsmod | grep 8187
rtl8187                53248  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbcore               149360  5 ndiswrapper,rtl8187,usbhid,uhci_hcd
jacatone@eMax ~ $ lsmod | grep ndiswrapper
ndiswrapper           196380  0 
usbcore               149360  5 ndiswrapper,rtl8187,usbhid,uhci

Don't quite know what this means? If Ubuntu is using the default rtl8187 wifi driver, how do I configure it to use the rtl8187B driver I installed with ndiswrapper?

---

### Post by Lostin60's on 2009-03-08
> **jacatone said:**
> I'm running Ubuntu 8.10. This version of Ubuntu has the Realtek 8187 wifi dongle driver but my wifi dongle takes the RTL 8187B driver, so I tried installing it's Win98 driver using ndiswrapper. What command would I use to determine if I'm using the ndiswrapper driver or the old 8187 one? If I'm using the old 8187 one, how do I make the change? Thanks.
Go to this post, it's excellent. [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) If ```
lshw -C network
```
If that shows the8187 driver see that links advice on blacklisting.


here is part of my ```
lshw -C network
```
this should be listed with the network1 info
  capabilities: bus_master ethernet physical wireless
       [COLOR="Red"]configuration: broadcast=yes driver=ndiswrapper+bcmwl5[/COLOR] driverversion=1.53+Broadcom,03/23/2006, 4.40.1 ip=192.168.2.2 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

if it lists the wrong driver then follow the instructions at the link..about 1/2 way down.


[COLOR="White"]aaa
[/COLOR]

---

### Post by jacatone on 2009-03-09
Thanks "Lostin60's", that was indeed a useful article. Unfortunately, it said my install of the Win98 rtl8187b driver was there using ndiswrapper, but when I blacklisted the default rtl8187 driver that came with Ubuntu 8.10, my wifi wouldn't connect. So, I'm kind of right back where I started.

jacatone@eMax ~ $ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8189) present (alternate driver: rtl8187)

---

### Post by Lostin60's on 2009-03-10
> **jacatone said:**
> Thanks "Lostin60's", that was indeed a useful article. Unfortunately, it said my install of the Win98 rtl8187b driver was there using ndiswrapper, but when I blacklisted the default rtl8187 driver that came with Ubuntu 8.10, my wifi wouldn't connect. So, I'm kind of right back where I started.

jacatone@eMax ~ $ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8189) present (alternate driver: rtl8187)

I might not have been clear..ok I wasn't clear..lol
Did you notice in the tutorial that you have to blacklist ssb also. As my
```
lshw -C network
``` showed my driver AND ndiswrapper. If it says your driver and something else, you need to blacklist the something else too. Usually the something else is "ssb" Also in the tut, see the part about updating the "initramfs" Hope this is more helpful.
[COLOR="White"]aa[/COLOR]

---

