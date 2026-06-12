---
title: "need help with realtek alc883 drivers"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by brijraj22 on 2008-12-08
i have a system with nvidia chipset nforce 610i/ge force 7050 with realtek alc883 hd audio.currently i get a very low volume on all applicatins,barely audible.i have maxed all volumes includng the pcm etc. but no result.also,i have a 5.1 speaker system and only one of the satellite speakers seem to work.does ubuntu give support for 5.1 speaker system and is there a way to increase the volume (by installing the driver for realtek alc883 perhaps)?
i'm pretty new to ubuntu (8.10),just installed it a couple of days back.like most of the windows users, dont have much idea about the terminal and its commands.so plz explain it in layman's terms.
looking forward to a reply.

---

### Post by DaveyG on 2008-12-08
Hey brijraj22, welcome to Ubuntu Forums!

To know exactly which nVidia Graphics Card and Realtek Audio Card you have, please paste the results of:

```
lspci
```

Also do a check in System -> Administration - Hardware Drivers, and select the required Drivers (if any listed)

Usually, most Drivers can be enabled/installed through "Hardware Drivers"

---

### Post by brijraj22 on 2008-12-08
result of lspci:
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)

the hardware driver section shows "Nvidia accelerated graphics driver version 177" as active. no other drivers shown.

---

### Post by DaveyG on 2008-12-08
I found another thread with possibly the same issue, but i'm not entirely %100 sure of how to solve it, as you're using 8.10..

[http://ubuntuforums.org/showthread.php?t=959505](http://ubuntuforums.org/showthread.php?t=959505)

It could well be a kernel related problem as posted in the Topic liniked above, as the user upgraded to 8.10.. I'll do some re-search and see what i can digg up for you :)

---

### Post by brijraj22 on 2008-12-08
thanks for the effort buddy.
by the way, i checked it nd found that its only my 5.1 speakers which seem to be having a problem with ubuntu. i plugged in my headphones(in the rear slot,along with the speakers) nd though the volume is low compared to vista,it is good enough.i think there is a problem of not supporting the 5.1 speakers (the speakers are running well on vista where i have a realtek hd driver installed and configured for 5.1 output)

---

### Post by brijraj22 on 2008-12-09
anyone can help me with this? how do i get the volume to go up on my speakers??? my speakers give an output of 48oo watts,good enough to wake up the whole neighbourhood (on windows) but i can hardly hear anything n ubuntu even with max volume.any suggestions?

---

