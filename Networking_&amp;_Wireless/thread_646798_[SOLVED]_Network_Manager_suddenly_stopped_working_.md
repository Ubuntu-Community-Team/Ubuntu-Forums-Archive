---
title: "[SOLVED] Network Manager suddenly stopped working in Ubuntu 7.10"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by DrewB on 2007-12-21
Hello,
The Wireless connection functionality in Network Manager in Ubuntu 7.10 has suddenly stopped working and I can not connect to my wireless network anymore. In fact NM doesn't even find any wireless networks when it runs and It used to find at least two others from the surrounding area.

I can connect via a wired connection to the wireless router (Netgear) but not wirelessly.

I have tried completely removing network-manager and network-manager-gnome and re-installing it but that didn't work.

I've run an Ubuntu live CD and couldn't connect to the wireless in that either. The wireless router is working because a Windows machine can connect to it fine.

I am running Ubuntu 7.10 on an AMD64 Gateway MX6440 laptop with Broadcom BCM4318 wireless controller.
I'm also using the ndiswrapper driver.
The output from lshw -C network is:

  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:90:07:43
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s


  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:8c:45:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,02/11/2005, 3.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Thanks a lot for any help anyone can give or any suggestions anyone has.
Andy

---

### Post by spd106 on 2007-12-21
Can you please provide the output these commands?

```
ndiswrapper -v
```

```
iwconfig eth1
```

```
sudo iwlist eth1 scanning
```

---

### Post by DrewB on 2007-12-21
Here you go:

```
ndiswrapper -v

utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 

```

```
iwconfig eth

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
sudo iwlist eth1 scanning
eth1      No scan results

```

Thanks a lot.

---

### Post by DrewB on 2007-12-22
So it seems that my wireless card can't find any access points anymore.

I think Ubuntu killed it!

I was browsing around when Firefox crashed (as its liable to do, especially when displaying Flash contnent.) Ubuntu then totally froze and I couldn't do anything, even shutdown, so I had to press the power down button to force it.
The next day I had this problem with my wireless card :(

---

### Post by spd106 on 2007-12-22
It's quite odd that ndiswrapper appears to be correctly configured and loaded, yet you aren't sending or receiving any data.

It might be a good idea to try the bcm43xx driver temporarily, just to verify that ndiswrapper is not at fault. There are instructions on the help wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Make sure that you unload ndiswrapper using this command before you enable the bcm43xx firmware.
```
sudo modprobe -r ndiswrapper
```

As long as you have bcm43xx blacklisted it won't be automatically loaded at boot, so this will just be temporary.

If bcm43xx doesn't work either, then it might be worth looking for maybe a hardware wifi switch in the wrong position?!?

---

### Post by gilf on 2007-12-22
Don't know if this thread on a recent flash plugin bug has relevance here, but:

[http://ubuntuforums.org/showthread.php?t=631178](http://ubuntuforums.org/showthread.php?t=631178)

     and confirmed bug report:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343)

---

### Post by DrewB on 2007-12-22
Thanks a lot for that I'll try using the bcm43xx driver.
Cheers!

---

### Post by DrewB on 2008-01-02
Hi again,
I tried the bcm43xx driver but that didn't work either, so its not the ndiswrapper that's at fault. For some reason my Wi-Fi card seems to have died!
I'm going to create a partition and install Windows XP and see if that can connect via Wi-Fi to see if its something wrong in Ubuntu.

---

### Post by DrewB on 2008-01-11
Hello again,
I installed Windows but that doesn't even find my Wi-Fi card!
At least when I boot into Ubuntu it can see the card, i.e It shows up in the Device\Hardware manager in in a ```
lshw -C network
``` listing. But it can't use it - it doesn't find any  access points and I've tried both the bcm43xx driver and ndiswrapper.
Its like it just died for some reason.
Does anyone have any clue as to what might have happened?
Thanks
Andy

---

### Post by spd106 on 2008-01-12
Try looking in the output of *dmesg* for errors.

Also, it could be hardware related, so perhaps reseating the card might help.

---

### Post by dicecca112 on 2008-01-12
Its the new network Manager update.  My broadcom will connect but dies on idle.  Search in Synaptic Network manager.  Downgrade the package to  0.65ubuntu16, and lock it at that version.

---

### Post by maglev89 on 2008-01-12
Mine's doing the same thing, I'am new to Linux so it's really been a experience. If I boot my Xp partition up it works just fine, but as soon as ubuntu is loaded up it doesnt. Ndiswrapper is showing the Card as being present and the driver installed properly. Yet their is a light on the front of my laptop which shows their is any activity with the card and it doesn't light up at any time, even when I scan for networks. Only happened after I upgraded to 7.10. I'm not trying to hijack your thread but I think this is definitely relevant.

---

### Post by quantumhobbit on 2008-01-18
I'm fairly new to Ubuntu so I don't know if this is relevant, but I had a similar problem where Ubuntu stopped showing any wireless networks (there are at least 30 in my area).  When I changed the setting to allow roaming mode under network settings everything started working again.

---

### Post by DrewB on 2008-03-01
> **spd106 said:**
> Try looking in the output of *dmesg* for errors.

Also, it could be hardware related, so perhaps reseating the card might help.

Hi you were right it was hardware related a wi-fi switch was in the wrong position so I just reset it and everthing's hunky dory now. Thanks for your help!

---

