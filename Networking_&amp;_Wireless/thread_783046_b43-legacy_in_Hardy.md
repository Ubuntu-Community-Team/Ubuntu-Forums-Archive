---
title: "b43-legacy in Hardy"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by wareagle on 2008-05-05
I upgraded from Gutsy to Hardy (using Kubuntu here, if that matters).  Wireless works but it is still using bcm43xx (which has some annoying bugs) and not b43.

Since my card is a 4306 r3 I would like to switch over to b43-legacy.

I tried blacklisting bcm43xx and installing b43-fwcutter, but it doesn't work.  It does not detect the b43 driver.

Any suggestions? :confused:

---

### Post by Ayuthia on 2008-05-05
Can you post your lspci -nn?  Not all 4306 cards are b43legacy.  I have a 4306 on my laptop and it is a 14e4:4320 rev 03 and it is using b43.

Can you also post the results for```
lsmod|grep -i -e b43 -e ssb -e bcm43xx
```

We can see what modules are being loaded.

---

### Post by wareagle on 2008-05-05
Files uploaded :)

---

### Post by Ayuthia on 2008-05-05
For now, try doing:
```
sudo modprobe -r bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
```
I am guessing that it is wlan0.  It could be eth1 also.

If this works, we will have to look at /etc/modprobe.d/blacklist and /etc/modules to figure out what is causing bcm43xx to load and not b43.

---

### Post by wareagle on 2008-05-05
sudo modprobe b43
FATAL: Module b43 not found.

---

### Post by Ayuthia on 2008-05-05
Can you post the results from the following:
```
lshw -C network
ls /lib/firmware/b43
```
I want to see the hardware information for your wireless to see what driver it is using and also want to see if the files were placed in the firmware for b43.

---

### Post by wareagle on 2008-05-05
```
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:00:78:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=128.195.4.64 latency=32 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 03
       serial: 00:90:96:b0:11:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
```

```
chris@tt3:/lib/firmware/b43$ ls
a0g0bsinitvals4.fw  a0g0initvals5.fw     a0g1initvals13.fw    b0g0bsinitvals4.fw  b0g0initvals4.fw    lp0initvals13.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals5.fw  b0g0initvals5.fw    pcm4.fw           ucode13.fw
a0g0initvals4.fw    a0g1bsinitvals5.fw   b0g0bsinitvals13.fw  b0g0initvals13.fw   lp0bsinitvals13.fw  pcm5.fw           ucode4.fw
chris@tt3:/lib/firmware/b43$ cd ..
chris@tt3:/lib/firmware$ cd b43legacy/
chris@tt3:/lib/firmware/b43legacy$ ls
a0g0bsinitvals2.fw  a0g0initvals2.fw  a0g1bsinitvals5.fw  b0g0bsinitvals2.fw  b0g0initvals2.fw  pcm4.fw  ucode11.fw  ucode4.fw
a0g0bsinitvals5.fw  a0g0initvals5.fw  a0g1initvals5.fw    b0g0bsinitvals5.fw  b0g0initvals5.fw  pcm5.fw  ucode2.fw   ucode5.fw
```

---

### Post by Ayuthia on 2008-05-05
> **wareagle said:**
> ```
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:00:78:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=128.195.4.64 latency=32 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 03
       serial: 00:90:96:b0:11:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
```

```
chris@tt3:/lib/firmware/b43$ ls
a0g0bsinitvals4.fw  a0g0initvals5.fw     a0g1initvals13.fw    b0g0bsinitvals4.fw  b0g0initvals4.fw    lp0initvals13.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals5.fw  b0g0initvals5.fw    pcm4.fw           ucode13.fw
a0g0initvals4.fw    a0g1bsinitvals5.fw   b0g0bsinitvals13.fw  b0g0initvals13.fw   lp0bsinitvals13.fw  pcm5.fw           ucode4.fw
chris@tt3:/lib/firmware/b43$ cd ..
chris@tt3:/lib/firmware$ cd b43legacy/
chris@tt3:/lib/firmware/b43legacy$ ls
a0g0bsinitvals2.fw  a0g0initvals2.fw  a0g1bsinitvals5.fw  b0g0bsinitvals2.fw  b0g0initvals2.fw  pcm4.fw  ucode11.fw  ucode4.fw
a0g0bsinitvals5.fw  a0g0initvals5.fw  a0g1initvals5.fw    b0g0bsinitvals5.fw  b0g0initvals5.fw  pcm5.fw  ucode2.fw   ucode5.fw
```

Well, that looks ok also.  Can you post the results for:
```
locate b43.ko
uname -r
```

EDIT:
Forgot to mention what I am requesting.  We are looking to see if the b43 module does exist.  The other thing that I want to make sure that we are running on the correct kernel.  Hardy is using 2.6.24 and b43 only comes in the 2.6.24 kernel or higher in Ubuntu.

---

### Post by wareagle on 2008-05-05
```
chris@tt3:/lib/firmware/b43legacy$ locate b43.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
chris@tt3:/lib/firmware/b43legacy$ uname -r
2.6.22-14-generic
chris@tt3:/lib/firmware/b43legacy$
```

---

### Post by Ayuthia on 2008-05-05
> **wareagle said:**
> ```
chris@tt3:/lib/firmware/b43legacy$ locate b43.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
chris@tt3:/lib/firmware/b43legacy$ uname -r
2.6.22-14-generic
chris@tt3:/lib/firmware/b43legacy$
```

There is the problem.  For some reason you are still running 2.6.22-14-generic.  That is the Gutsy kernel.  Can you check in your /boot/grub/menu.lst and see if there is an entry for the 2.6.24 kernel?  That is the one that we need to boot.

---

### Post by wareagle on 2008-05-06
LOL, newb mistake.

When I was upgrading it asked me if I wanted to replace my menu.list and I said no because I had modified it.

I fixed grub, and now wireless seems to at least work better than Gutsy.  Signal power levels are much more accurate.  In particular, I have a problem with my school's network, which uses multiple access points in different subnets.  My card keeps (kept?) switching APs aggressively and every time it switched to one on a different subnet, I would lose my connection and have to run dhclient.

---

### Post by Ayuthia on 2008-05-06
Have you tried connecting from the terminal?  I am thinking that instead of accessing by SSID, try accessing by AP (never tried it though):
```
sudo iwconfig wlan0 ap 11:aa:22:bb:33
sudo dhclient wlan0
```You might have to quit out of Network Manager because it might try to switch you.

---

### Post by wareagle on 2008-05-06
Yes, I have tried that.

Apparantly the AP command in some wireless cards (Broadcom included) is only a suggestion.  It appears that it will switch the AP, but as soon as the card detects another IP with higher signal strength, it will switch to it anyway.

If the source code of Broadcom's firmware could be modifed, the problem could be resolved.  But the chances of that happening are about the same as those of having Windows XP's source released.  :(

---

### Post by zeitler on 2008-09-11
Hi! 
I was looking how to activate my wireless (Broadcom 4306) and I found this.

Before I had Ubuntu 7.10 and my wireless work fine thanks to a tutorial I've found ([http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)). Now I have updated to Hardy 8.04 and the wireless doesn't work anymore. I have been looking over the web and I've founded that hardy have something to protect from a bug that overrides ndiswrapper with ssb and I've insert the commands to change that and even that still doesn't work. 

Can you help me?

Thanks.

---

### Post by wareagle on 2008-09-11
Can you post the contents of /etc/modprobe.d/blackist?

---

