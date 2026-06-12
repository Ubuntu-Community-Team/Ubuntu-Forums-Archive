---
title: "Ubuntu Light, Dell M101z, Triple Boot"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by netpage on 2011-01-18
Hi,

I am about to purchase a Dell M101z laptop that reportedly comes with Ubuntu Light as an option for fast "instant-on" access to the internet.

Will it be possible to install a full version of Ubuntu along side this and Windows 7, without affecting Ubuntu Light?

I am assuming that UL will act as any other OS and therefore I will have a triple boot computer.

Any advice would be appreciated.

---

### Post by NightwishFan on 2011-01-18
Why not just install Ubuntu? I am not sure light offers much more than standard Ubuntu other than default configuration.
[http://www.canonical.com/sites/default/files/active/images/Ubuntu%20Light%20Datasheet.pdf](http://www.canonical.com/sites/default/files/active/images/Ubuntu%20Light%20Datasheet.pdf)

---

### Post by netpage on 2011-01-18
My understanding is that Ubuntu Light is for instant-on access, for access to the internet, but yo can not add any programs to it.

I would then like to install a full version of Ubuntu for my other tasks but keep Windows 7 for when I need to know how luck I am using Ubuntu :) OR I need iTunes.

---

### Post by NightwishFan on 2011-01-18
Unless you have a particular need for Ubuntu Light, I say just dual boot normal Ubuntu and Windows.

---

### Post by prahari on 2011-02-20
I purchased a Dell M101z 2 months ago (dual core, Ram 2GB, HD 250 GB). I installed Ubuntu 10.04 alongside the existing Windows 7 and Ubuntu light, however the boot experience and the disk partitioning became really messy (in addition to W7 and UL, you also need to take into account the Dell recovery partition). After two days, I wiped out everything (including the recovery partition) and installed Ubuntu 10.04. Everything worked out of the box including Wi-Fi, BlueTooth, Webcam, and graphics card (you will need to use proprietary drivers though, and tweak grub to have suspend working).

---

### Post by netpage on 2011-02-20
I am halfway through setting it up and the partitions are a bit messy.  I ended up converting the recovery partition to the swap and increasing the Ubuntu Light partition and installing Ubuntu 10.10 NBR on this.  For some reason 10.04 caused problems with the cursor freezing.

WiFi worked after installing proprietary drives but these would only install after Update Manager was run.

I had to edit the GRUB loader to add an entry for Windows, however I cannot boot into Windows and the MBR is missing.  Working on this now.

---

