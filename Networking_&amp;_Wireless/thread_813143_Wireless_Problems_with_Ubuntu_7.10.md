---
title: "Wireless Problems with Ubuntu 7.10"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by corruptsystem on 2008-05-30
Hello everyone, 
    I tried to play around with the new distro of Ubuntu (8.04) and found it a little buggy here and there.  I was just wondering if it were at all possible to grab the wireless drivers from 8.04 and use them with 7.10.  It sounds like a stretch, but something tells me it can be done.  The problem I am having is that I have a generic USB wireless adapter.  However, in 8.04, wireless works perfectly fine without the installation of any additional drives.  Just the base install of Ubuntu 8.04 and the USB Wireless worked fine.  When I installed 7.10, the only network adapters it found was my Wired Connection and a Modem (I don't have a modem installed).  I was just wondering if it's at all possible to get 7.10 to recognize that wireless adapter like 8.04, because as I said, I don't really know where to go for installation because the adapter is generic with no indication of a vendor or anything on it either.  Thanks a lot for everyone's help.  I really appreciate all you guys do for me on here.  Thank you

---

### Post by Sam Lars on 2008-05-30
I'm pretty sure that what you want is in the kernel, so the only option would be to run the Hardy kernel in Gutsy, but that might also bring with it some of your bugs.
Specifically, what card do you have?

---

### Post by corruptsystem on 2008-05-31
Yeah thats what I was thinking is that I'd possibly bring about some issues that Hardy has with it.  If I could just use the wireless aspect of Hardy in Gutsy, that would be great because the wireless worked great in Hardy.  Even the display drivers for me were working well enough.  I have another post on here that deals with my issues there.  I have an ATI Radeon X1550 Video card and cannot enable hardware acceleration to enable Compiz.  But that's a whole other issue.  To be honest, I'm not sure which wireless card I have.  Like I said, it is a generic one that I picked up on eBay for a couple bucks.  It has a driver CD for Windows, but no tarball or anything for Linux (naturally).  All the card says on it is "sn: 320000050157041604697" and "mac:  0060B3ADDD64" which Google tells me nothing about.  Thanks for the prompt response.  Maybe there is something you can do to help. I really appreciate it.

---

### Post by Ayuthia on 2008-05-31
You might try going to the Terminal and try typing:
lsusb

It might provide the information about your card.

---

### Post by Sam Lars on 2008-05-31
There's also a possibility of recompiling the Gutsy kernel to include your wireless drivers, if you're up for it.

---

