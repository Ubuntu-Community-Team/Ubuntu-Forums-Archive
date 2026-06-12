---
title: "Can i dual bot ubuntu 8.1 and vista?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by cranky1984 on 2009-03-08
Hey folks,

Im a newbie to the linux community.

I burnt the live cd 2 days back with the help of a lotta good advice from the folks here..I ran it and simply loved ubuntu.

I was just wondering that instead of completely uninstalling vista , can i install ubuntu over vista and use both the os's as required? its just that I need some of the softwares on vista which I am currently working with. but i soo badly wanna move over to ubuntu..

can anyone tell me how would i do it and would it b a pain to get it up and running?

thanks in advance..

My configuration is 
AMD AthlonTM 64 X2 Dual-Core processor TK-57 (1.9GHz/256KB)
2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 Dimm
ATI Radeon® Xpress 1150 256MB HyperMemory&#33922; (integrated)
120GB 5400RPM Hard Drive
8X DVD+/-RW with double-layer DVD+R write capability, Cyberlink Power DVD
Integrated Audio
Dell Wireless 1490 802.11a/g Wi-Fi Internal Card

---

### Post by bailbath on 2009-03-08
Yes you can there are plenty of guides on the internet or on this forum.
I have not done it but there will be plenty of peeps on here that have.
[http://vista.blorge.com/2008/02/22/how-to-dual-boot-vista-with-ubuntu/](http://vista.blorge.com/2008/02/22/how-to-dual-boot-vista-with-ubuntu/)

Here's one guide but there are plenty more so google and take your choice.
Always back up your important files first.
Ian

---

### Post by bailbath on 2009-03-08
Plus do some research on your hardware so you are prepared for any problems that may lie within!
Ian

---

### Post by Henry70 on 2009-03-08
Ciao Cranky1984,

In short: Yes, you can configure a dual boot system with Vista and Ubuntu. I recently bought a quad-core with Vista pre-installed and need Vista for certain apps. I've installed Ubuntu 8.04-AMD64, and only intervened in the installation option, once the setup installer is asking for the disk setup. If set right, Ubuntu will automatically install grub (boot-loader) and it works.

Btw, I've just upgraded to 8.10 and everything still works fine.

---

### Post by philinux on 2009-03-08
Backup anything important first!!!

---

### Post by fmfrisch on 2009-03-08
You can also install Ubuntu "within" vista. Just insert the live CD while you are booted in vista and choose the install within option.. I got problems when doing dual boot because the windows bootloader tried to write over GRUB. I find the within vista option more reliable. This of course depends on if you have 2 seperate harddrives for the different OS'.

---

### Post by philinux on 2009-03-08
There is another way. Shrink vista with it's own tool. Install ubuntu to the spare space. At the last step use the advanced button and install grub to the ubuntu partition not the mbr.

Then use easybcd to edit vista's bootloader and add an entry to point to grub in the linux partition.

---

### Post by geirha on 2009-03-08
This guide on switching from windows to ubuntu is pretty good. It covers both removing windows and installing only ubuntu, and installing ubuntu along side windows (dual booting).
[https://help.ubuntu.com/8.10/switching/index.html](https://help.ubuntu.com/8.10/switching/index.html)

---

