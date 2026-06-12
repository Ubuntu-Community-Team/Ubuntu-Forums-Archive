---
title: "half mini wifi card undetect problem at lspci"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by oguzy on 2008-07-30
Hi,

I have a AzureWave AW-GE703H PCI-E Half Mini wireless card. I am trying to use it under Hardy. 

When i run the command lspci i dont see any related wifi network card information. In dmesg or lshw there is no output also. 

I read the Wireless Trouble Guiede at Ubuntu Wiki, and tried the pci argument also but they didn@t help me to see my car at lspci. 

So do i need to install the driver of the card to see it at the lspci output or does it detected and driver is needed only for running wireless connection?

Another thing is the firmware thing. Do i need to install a firmware to make detected by my Linux kernel?

---

### Post by oguzy on 2008-07-31
Ok, i found the driver that makes it run. 
Here: [http://launchpadlibrarian.net/16098501/rtl8187se_linux_26.1016.0716.2008.tar.gz](http://launchpadlibrarian.net/16098501/rtl8187se_linux_26.1016.0716.2008.tar.gz)

---

### Post by chili555 on 2008-07-31
Even withoiut a driver, it should show up in *lspci* or *lshw* and, probably, both. You can certainly compile and install the driver, but if the computer is unaware of the device, I don't think it will help. Is there an option to enable or disable wireless in the computer's BIOS? Is the card installed securely?

If you decide to compile this, you will need to install *build-essential* and linux-headers matching your running kernel. If you have any questions about how to proceed, post back. 

It does compile without error.

---

