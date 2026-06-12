---
title: "fresh 13.04 install wifi not working"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by Higgins909 on 2014-02-18
During boot I get the error on the black screen with some white text that is kinda just flashed by, then it boots.

In around 11.?? and 12.?? I had no Issues with getting wifi, but may had to of plugged into router to download driver.

I tried updating to latest software.

It says something about **wireless**.**kernel**.org but I cant read that fast.

Thanks,
Higgins909

---

### Post by Bucky Ball on 2014-02-18
And the bad news is that 13.04 is no longer supported. As you have just installed, this is not so bad. Please install 12.04 LTS or 13.10, both directly upgradeable to 14.04 LTS when it is released in April (12.04 LTS is supported to 2017 incidentally, 13.10 for another five months). 

13.04 will no longer receive updates and this includes security updates, so may be a good thing you can't get online with it! ;)

---

### Post by Higgins909 on 2014-02-18
I guess thats cool, but is it not possible to go from 13.04 to 13.10? I know I somehow did something like that b4.  How do you find out about this stuff? because I want to always have the support, without having to do a fresh install, and having up to date stuff is nice too.

---

### Post by Bucky Ball on 2014-02-18
You can have a look [HERE]("https://wiki.ubuntu.com/Releases") for supported and unsupported releases. I stick with LTS myself (but have another three or four installs as playthings and testing) because of stability and long-term support. Interims don't suit as I need a reliable production/work environment that I know is not going fall over with the next update. ;)

Yes, I think that would be possible to upgrade to 13.10 from there, if the update manager will still give you the option. In update manager, if you set it to notify of all new releases, it should present you with '13.10 is now available' at the top of the GUI. But of course, you need to be online for any of this to happen. :-k

Could you post the output of this please:

sudo lshw -C network

... and we'll see if we can get that working and find out. i know it's a bit of a hassle as you'll need to copy the output to a usb. Sorry. ;)

---

### Post by Higgins909 on 2014-02-19
I reinstalled 13.10 it seems it was allready installed, redid updates  (thank god I have my own local proxy!) but it seemed a bit different on  install.
after updates looking in the drivers thing I saw my wifi  card this time, at first it wouldn't connect to wifi even after  restarting, then I disable wifi, enabled it again, and it connected.  strange.

---

### Post by Bucky Ball on 2014-02-19
Well, sounding good so far. When you feel confident this is stable, please mark this thread as solved. If it starts playing up again, report back.

It still persists after re-boot? If so, that's always a good sign. Can you post the output of the command I gave previously now, please?

sudo lshw -C network

;)

---

### Post by Higgins909 on 2014-02-19
Haven't played with the laptop that much, but I had to boot as I dont got a battery and unplug it when not in use.  May keep the thread open a day or two more.
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:80:98:b6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141  (r415941) ip=192.168.0.14 latency=0 multicast=yes wireless=IEEE  802.11abg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:73:2f:4c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:44 ioport:de00(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f003ffff

```

---

### Post by Bucky Ball on 2014-02-20
All present and correct. I'm predicting you will have no issues with this for the near future, but all good by your output. ;)

Just a note, it has labeled the wireless connection 'eth1' rather than 'wlan0', which would be more expected. This is no big deal or problem, but just be aware that how-tos and tutorials etc. will generally refer to the wireless connection as 'wlan*'. Just replace with 'eth1'.

---

