---
title: "no adapter found with 18.04"
date: 2020-01-08
forum: Networking &amp; Wireless
---

### Post by diewhilelive on 2020-01-08
Hello,

I just installed Ubuntu 18.04 on my MSI Modern 14 A10M and for some reason I cannot get the WiFi adapter to work. I previously installed Ubuntu 19.10 but I ran into a lot of problems, starting with overheating, battery drains and some incompatibility with software I use for college (Cisco, what a surprise).
I also installed W10 to update the BIOS and I couldn't use the WiFi until I installed a Intel Wireless-AC 9560 driver. I've found some related issues online but most solutions don't work for my because this particular laptop has no Ethernet ports (and getting a USB adapter or something is just ridiculous).

Hope someone can help with this,
Cheers

---

### Post by mörgæs on 2020-01-09
Hi, welcome to the fora.

If Ubuntu 19.10 caused problems I suggest you do a fresh install (not upgrade) of one of the other 19.10 Buntus, say X/Kubuntu.

---

### Post by guiverc on 2020-01-09
If you don't have an ethernet port; you can download the packages required (`wget`) , write them to a thumb-drive, mount it on your laptop and then install.  You'd be doing the same thing on a microsoft windows install in far more cases than Ubuntu (each OEM tends to re-spin windows for to avoid this issue).

You also didn't say which ISO of Ubuntu 18.04 LTS, if you used the original ISO (2018-April release), or a later 18.10 (18.04.2) software stack in HWE, or 19.04 (18.04.3) software stack. The 19.10 HWE software stack is provided in 18.04.4 which currently is in QA-testing and won't be released for awhile (but is always an option).

---

