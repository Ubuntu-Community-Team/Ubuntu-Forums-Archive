---
title: "Installing Wireless on HP Pavilion 6744ca"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by HustlinHard on 2008-05-05
Hi guys, I've searched and tried all the methods I could get my hands on and just can't seem to get my wireless working on my HP Pavilion 6744ca.  Could someone spend a minute and explain step by step exactly how i should set it up, including what drivers to download (Which i would have to do on my other computer since there is no internet obviously on the other one) and everything.

I have Ubuntu 8.04 installed, and basically the wireless network connection shows up in the top right under wireless networks.  But when I try to connect, it looks to me that it just times out.  Also the light on the laptop signifying whether wireless is on or off, is red (instead of blue) which means it is off.


I hope I've given enough information for someone to guide me through this.  Thanks in advance.

---

### Post by Ayuthia on 2008-05-05
HP laptops have various wireless cards installed (Broadcom, Intel, Atheros).  Can you see if you can figure out which type you have?  You can do this by:
```
lspci -nn
```This will list out your pci devices name along with their id numbers.  Look for something like Network Controller, Ethernet Controller, or wireless.  Please post the results that you find and we can help point you to a guide that might help.

---

### Post by HustlinHard on 2008-05-05
Thanks for the response, here is the lspci -nn results


> 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1) 
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61) 
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01) 
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12) 
07:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
07:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff) 


---

### Post by Ayuthia on 2008-05-05
You might try installing linux-backports-modules-2.6.24-16-generic.  Since you don't have a connection, you might have to go to packages.ubuntu.com and get the package from there.

Here is a link to it: [http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic)

You can download the package to your home directory and then do the following:

If you are using 32-bit
```
cd
sudo dpkg -i linux-backports-modules-2.6.24-16-generic_2.6.24-16.14_i386.deb
```

If you are using 64-bit
```
cd
sudo dpkg -i linux-backports-modules-2.6.24-16-generic_2.6.24-16.14_amd64.deb
```

dpkg -i is the .deb installer for Ubuntu.  It will check to see if your computer has all the dependencies and then will install it if the dependencies are met.

Hope that works for you!

---

### Post by HustlinHard on 2008-05-05
i tried typing the command and it tells me "cannot access archive: No such file or directory"


how exactly do i type it?

Basically I went into terminal,
then i typed cd - enter
and sudo dpkg -i linux-backports-modules-2.6.24-16-generic...

---

### Post by HustlinHard on 2008-05-05
actually i just double clicked it it was a self-installer and it installed.

But basically the same thing keeps happening, I try to connect, punch in the WEP passcode, and it tried to connect for about 30 seconds then prompts me for the WEP again.

---

### Post by Ayuthia on 2008-05-05
You might try turning off the encryption and see if you can connect.  If you can, then we will need to see how to connect using WEP.

---

### Post by zubairw on 2008-05-06
i have an intel pro/wireless 3945bg card. ubuntu detects the card just fine but the network manager dosent find any networks. is there a driver issue there too? do i need to install a package or something? i have ubuntu 8.04 aswel.

---

### Post by Ayuthia on 2008-05-06
> **zubairw said:**
> i have an intel pro/wireless 3945bg card. ubuntu detects the card just fine but the network manager dosent find any networks. is there a driver issue there too? do i need to install a package or something? i have ubuntu 8.04 aswel.
You might try doing the thing I suggested above also.  I have seem people install this and things turned out well, but I have heard that there are some issues also but it is mainly with the LED.

---

### Post by zubairw on 2008-06-17
i tried the steps. i can detect my wifi card fine but it dosent find any wifi networks. can it be something to do with my router?

---

