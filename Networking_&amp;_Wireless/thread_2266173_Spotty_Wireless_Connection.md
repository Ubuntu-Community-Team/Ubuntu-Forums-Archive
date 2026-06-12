---
title: "Spotty Wireless Connection"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by cobras on 2015-02-20
Hey Folks,

I'm running Ubuntu 12.04 fully udpdated on an Inspirion 6000.

Everything's been fine, until recently when I've been unable to gain a wireless connection.  Wireless networks register just fine, but I can't seem to get online.  A few minutes ago I seemed to finally connect but the browser wouldn't load a page.  The problem has persisted over any wireless network I've accessed.  I'm posting this with a wired connection.

Any suggestions would be most welcome.

I should probably mention that this has gone on for several days and have been able to connect once or twice but mostly not.

---

### Post by DCO on 2015-02-20
What kind of computer are you using? If it's a Dell like my laptop or any any other computer that uses a broadcom card, you could be having driver issues. My connection worked for a while too before I wound up with that problem.

To find out, use the command in terminal:
```
lshw -C network
```

and hit enter to ignore the warning that it should be run as super-user (or if it doesn't let you for some reason use sudo. - it let me just hit enter to get the information)

post the results back here.

---

### Post by cobras on 2015-02-20
Apparantly, "output may be incomplete or inaccurate", but here it is.  I've got a Dell Inspiron 6000, which I've upgraded to the max of 2 megs of RAM.

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: 00:12:3f:ec:20:95
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.9 latency=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth3
       version: 05
       serial: 00:13:ce:40:e6:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.17 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfdfd000-dfdfdfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by DCO on 2015-02-20
Yep, broadcom like I thought, let me find again the link that helped me since it looks like you have a different model than mine.

When I find that page I'll edit this post with the link.

Didn't take as long as I thought it would. here's the link that helped me sort mine out.
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

I know your pain, even newer models have this issue, I'm using an N7010

---

### Post by cobras on 2015-02-20
Maybe i"m misunderstanding the output, but it seems to me that my ethernet interface is by Broadcom, but my wireless interface is by Intel.  I should have probably mentioned that a couple of months ago I replaced the wireless card and it worked perfectly until recently.  I have to believe that a recent Ubuntu update went awry.

---

### Post by DCO on 2015-02-20
I'm not a networking expert, so I could be mistaken. But that reads like the overall controller (the part that interfaces with the driver) is Broadcom, and the card itself interfaces with the controller. 

That link I gave you though _*SHOULD*_ help you figure out the exact driver combination you need.

---

### Post by cobras on 2015-02-20
Thanks DCO.  Took a close look a the thread.  Not what I need.

---

### Post by jeremy31 on 2015-02-20
cobras, can you look at the sticky post. before posting in networking & wireless [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and run the wireless script and post results?  It might be easier to find an answer for you

---

