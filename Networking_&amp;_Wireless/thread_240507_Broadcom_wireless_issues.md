---
title: "Broadcom wireless issues"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2006-08-21
lspci | grep Broadcom\ Corporation
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

compaq presario v2000; amd turion 64 (for some reason x64 software doesn't work on my computer so i have i386 stuff installed)

i've basically used these two threads:
[190177]("http://www.ubuntuforums.org/showthread.php?t=190177")
[197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

so i have ndiswrapper installed as well as the drivers **BCMWL5.SYS** and **BCMWL5.INF**

my network connection lists both the eth0 and eth1 connections.

here is the info from "Network Tools - Devices" for eth1:

```
Interface Information
Hardware address: 0:14:a5:6b:ba:cd
Multicast:               Enabled
MTU:                     1500
Linkspeed:             Not Available
State:                    Active
```

i can't actually get online with the wireless adapter. when i press the WiFi button on my computer, the light blinks perpetually- something that never happened on windows- or it turns off completely.

i would greatly appreaciate any suggestions or assistance. i'm thinking that it might be easiest to just buy a new card and put it in the now vacant pcmcia slot.

---

### Post by truwrecks on 2006-11-03
> **dbbolton said:**
> lspci | grep Broadcom\ Corporation
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

compaq presario v2000; amd turion 64 (for some reason x64 software doesn't work on my computer so i have i386 stuff installed)

i've basically used these two threads:
[190177]("http://www.ubuntuforums.org/showthread.php?t=190177")
[197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

so i have ndiswrapper installed as well as the drivers **BCMWL5.SYS** and **BCMWL5.INF**

my network connection lists both the eth0 and eth1 connections.

here is the info from "Network Tools - Devices" for eth1:

```
Interface Information
Hardware address: 0:14:a5:6b:ba:cd
Multicast:               Enabled
MTU:                     1500
Linkspeed:             Not Available
State:                    Active
```

i can't actually get online with the wireless adapter. when i press the WiFi button on my computer, the light blinks perpetually- something that never happened on windows- or it turns off completely.

i would greatly appreaciate any suggestions or assistance. i'm thinking that it might be easiest to just buy a new card and put it in the now vacant pcmcia slot.

I'm having the same issue on my Gateway MX7025.  I had the Wifi working, then I shutdown the laptop. When I started it later I started having the same problem.  The WiFi power light flashes constantly, and the machine slows WAY down.

Can someone shed some light on this?

Thanks.

---

### Post by dbbolton on 2006-11-13
i got it to work by checking all of the connection's settings and making sure they were the same as those for my router (linksys)

i just typed in the router's ip address in firefox (it prompts for password) to get to the settings.

---

