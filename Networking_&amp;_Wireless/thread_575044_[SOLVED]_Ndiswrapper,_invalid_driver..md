---
title: "[SOLVED] Ndiswrapper, invalid driver."
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by CapitanYochua on 2007-10-13
I am trying to get internet working on my 050d:705c Belkin usb wireless network card. I copied the entire Driver folder on the installation CD onto my computer. 
 I ran the command:
   sudo ndiswrapper -i ~/Driver/BLKWGU.inf
After I check it with:
  ndiswrapper -l
It says invalid driver.
What should I do?  Please help.

---

### Post by kevdog on 2007-10-13
Is the .sys and .inf file located in the same directory???  What is the name of the .sys file?

---

### Post by CapitanYochua on 2007-10-13
Well in the whole directory there are a few .sys files. BLKWGUXP.sys    BLKWGU2K.sys  BLKWGU9X.sys
As well as a few other files that aren't .sys or .inf. And yes, they are in the same directory. But, I must add that the first time I did it with just the .inf on my desktop, and I tried it with the whole directory (with .inf and .sys) the second time which just gave me "driver already installed" or something like that. Thanks   for the quick response.

---

### Post by CapitanYochua on 2007-10-13
Also, the weird thing is that network manager says that I'm connected, but I'm not really able to use the internet in anyway.


Edit: It did say it was connected. I rebooted the computer, and it no longer says it's connected.

---

### Post by kevdog on 2007-10-13
Clear out all bad drivers that were installed with

sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo modprobe ndiswrapper

Check what you have with ndiswrapper -l

---

### Post by CapitanYochua on 2007-10-13
Okay. I did that, and then retried the ndiswrapper -i /path with the directory that had all those files (.sys and .inf). And restarted my computer. Now it works!!! (:
 Thank you so much. This made my day.

---

