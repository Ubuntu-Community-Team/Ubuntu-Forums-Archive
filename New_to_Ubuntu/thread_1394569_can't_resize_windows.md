---
title: "can't resize windows"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by soft-e on 2010-01-30
Hello,
 
I'm new toLinux/Ubuntu. I installed Ubuntu 9.10 on my Dell desktop. I wiped out the windows OS. I didn't need it. I also have the XP cd with me if I have to reinstall . I had a feeling that my computer wasn't able to handle the sophisticated graphics that came with this release so I installed UBuntu in the safe mode, with minimal graphics. I've noticed, that during the install process itself,  the display's were very messed up. I couldn't get to some of the buttons etc. I'm now even forced to key in a user id and password during login (an undesirable result of my display problem). Later while watching "youtube", it looks like as though, the video gets diplayed in wide screen. I can see the top half, but to see the bottom half, I have to scroll down and when I do that, I can't see the top half. When I do a full screen, the experiecen is normal. I also have a prolem with my general experience with web browsing as well using Mozilla Firefox. I've not used Fireforx before. On my window vista (on a different computer), when I go to cnn.com (I'm using Internet Explorer), most of the page is displayed, and I have a vertical scroll bar to show me the remainging. But on Firefox/Ubuntu, very little part of the page is displayed. I also have a horizontal bar. I have to use the horizontal and veritical scroll bars to view the contents. When I hooked my laptop that runs Windows and IE to the montior that I'm using for Linux/Ubuntu, indicating that something is wrong with Ubuntu/Firefox. 
 
Please help
soft-e

---

### Post by NightwishFan on 2010-01-30
May I ask what model your graphics hardware is? To find out on Linux, go to a terminal and type:
```
lshw -c video
```

---

### Post by soft-e on 2010-01-30
Hello NightwishFan,

Thank you for your response. I'm having a problem responding because of the visual layout of the screen. Here's the information:

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e0000000-e7ffffff(prefetchable) memory:ee000000-ee07ffff

-soft-e

---

### Post by *Raz0r* on 2010-01-30
I had a similar problem when installed the new 9.10 Ubuntu. My computer freezes every time when opening random applications. So I had to quickly disable the Compiz Fusion Graphic Effects. After that all works fine for me now.

---

