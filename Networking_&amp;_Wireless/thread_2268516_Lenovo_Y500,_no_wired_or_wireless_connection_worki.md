---
title: "Lenovo Y500, no wired or wireless connection working"
date: 2015-03-09
forum: Networking &amp; Wireless
---

### Post by asheesh2 on 2015-03-09
Hi,
I have installed ubuntu 14.04 2 days back, I am using it first time, but after many tires and going through threads I am not able to connect to internet.
Neither wired not wireless, for wired connection it tries to connect always end up with message " Disconnect - you are now offline" 
Laptop details are 
Lenovo y500, 1.5 GB RAM, so installed 32 bit vision, for wifi I can not see hardware switch ligh on , so not sure if thats the reason but atleast if LAN can work I can look for solution for wifi
highly appreciate if someone can suggest some solution, I dont want to move to windows 
 other may be useful information are

Intel® Celeron(R) M CPU 520 @ 1.60GHz
Intel® 945GM x86/MMX/SSE2
32-bit
 
$ lspci -n | egrep '0200|0280' | awk'{print$3}'
14e4:4311
10ec:8139
 
 
 
             for eth0:
            Supportedports: [ TP MII ]
            Supportedlink modes:   10baseT/Half 10baseT/Full
                                    100baseT/Half100baseT/Full
            Supportedpause frame use: No
            Supportsauto-negotiation: Yes
            Advertisedlink modes:  10baseT/Half 10baseT/Full
                                    100baseT/Half100baseT/Full
            Advertisedpause frame use: No
            Advertisedauto-negotiation: Yes
            Speed:10Mb/s
            Duplex:Half
            Port:MII
            PHYAD:32
            Transceiver:internal
            Auto-negotiation:on
Cannot get wake-on-lan settings: Operationnot permitted
            Currentmessage level: 0x00000007 (7)
                                           drv probe link
            Linkdetected: yes

---

### Post by chili555 on 2015-03-09
Please see post #7 here: [http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)

You have the same device and require the same fix.

---

### Post by asheesh2 on 2015-03-09
Thanks a lot Chili !! 
It fixed my wifi, but somehow for Ethernet result is same, I guess need another driver for LAN, atleast I am connected now can look for other fix.
still to fix touchpad, chrome, hope will get fix with not much difficulty

---

### Post by chili555 on 2015-03-09
> **asheesh2 said:**
> Thanks a lot Chili !! 
I guess need another driver for LAN, atleast I am connected now can look for other fix.
Yes, indeed. Your ethernet device is this:```
10ec:8139
```Google it along with Ubuntu and post back if you get stuck.

---

### Post by asheesh2 on 2015-03-10
Hi,
As best of my knowledge, I updated the kernel version, but no success for Ethernet LAN connection, also some times touch pad starts working and some times don't work, so need to rely on external mouse. couldn't get solution for it

---

