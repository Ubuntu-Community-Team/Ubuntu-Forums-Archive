---
title: "display problems with nVidia GeForce2 card"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by bezbelin on 2010-09-02
Hi,

I am a windows user and just plunged into world of linux. I went through the forum for this specific problem of mine (thank you guys for ur excellent support) and found some options which I tried, but could not solve. So heres my issue.

I was using windows XP on an old system and installed Ubuntu 9.04 (jaunty) in a dual boot fashion from within windows. I have an AMD Athlon XP 2400+ processor, ASUS motherboard with onboard graphics and Samsung SyncMaster 753s monitor. Now the max. display resolution is low with 800x600 (4:3) enabled. Here's what i obtained with lshw -C display command

*-display UNCLAIMED     
       description: VGA compatible controller
       product: NVCrush11 [GeForce2 MX Integrated Graphics]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5

In Hardware drivers i found nVidia accelerated graphics driver (version 96) which i activated, after which i could opt for higher resolutions. But this also caused a "trailing effect" in all windows that i opened later plus "shadow windows" being retained after closing windows and there was marked delay in cursor movement. I had to deactia6te this.
Later I found an Nvidia document which said I need to get a specific driver -Linux-x86-96.43.18-pkg1.run which i installed but the same problems persisted. So i had to un-install the same.

Now I am only a 2 day old user in Linux environment and getting to know the nuances. Please let me know in what way I will be able to find a solution to this. Thanks in advance.

---

### Post by Elfy on 2010-09-02
Do you have Visual Effects set? Try setting to none - System - Preferences - Appearance - Visual Effects tab.

---

### Post by khelben1979 on 2010-09-02
There could be a hardware related problem. Have you ever opened the case and checked cooling fans and the amount of dust inside etc etc.?

The accelerated nVidia driver requires more power from the graphics and because of this more heat develops inside the case and the power strain on your [power supply]("http://en.wikipedia.org/wiki/Power_supply") also increases as a effect.

---

### Post by bezbelin on 2010-09-02
Hi, Thank you for reply

_to khelben1979@_ 
The cabinet is as such open. I admit there's dust but not to hamper the movement of fan. All these works well in windows xp even now. All other functions are fine- including playing movie files. Only problem is I cannot set a higher resolution than 800x600 due to which whatever window i open occupies a large area on my desktop (even mouse right click occupy 3/4th area!!!) . 

_to forestpiskie@_
The Visual Effects is set to "none" and though I tried it gives similar problems when I change it to "Normal".

Please let me know what I should do. The graphics card is an onboard one (use Asus motherboard). Thank you all.

---

### Post by khelben1979 on 2010-09-02
You should be able to modify the X configuration file to get larger screen resolutions.

You might find [this]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") interesting. Scroll down the page and look at how they have done.

---

