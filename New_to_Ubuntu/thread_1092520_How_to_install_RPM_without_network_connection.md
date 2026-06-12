---
title: "How to install RPM without network connection"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by hwatari on 2009-03-10
I bought a MSI netbook u100 and installed Ubuntu 8.10 on a dual boot but WLAN dosn't work, so Ubuntu is not connected to Internet.
I downloaded a WLAN driver from MSI to a flash drive using Windows but I can't rpm the package since I'm not connected to Internet and can't apt-get rpm package, a classic catch 22, wouldn't you say ?
Can someone tell me how I can get a rpm package in this circumstance ?
Thanks,
Hiromichi

---

### Post by hwatari on 2009-03-10
Forgot to mention but the driver is for

Linux: For SUSE Linux Enterprise Desktop 10 SP1 only.

I am hoping that the driver also works for Ubuntu as well.
Am I correct in making the assumption ?

---

### Post by lamalex on 2009-03-10
Ubuntu doesn't use rpm as its package, we use .deb packages which are quite different. You can try and convert with the program 'alien' but that's not always successful. Can you post the output of lspci (open a terminal and enter that command) so we can see what type of network card is in your netbook? That will be helpful for fixing your problem.

---

### Post by hwatari on 2009-03-10
> **Iamalex said:**
> Ubuntu doesn't use rpm as its package, we use .deb packages which are quite different. You can try and convert with the program 'alien' but that's not always successful. Can you post the output of lspci (open a terminal and enter that command) so we can see what type of network card is in your netbook? That will be helpful for fixing your problem.


Iamalex,
Thank you very much for your reply,
here is the output, I believe RaLink is my wireless device.

-----------------------------------------------------------------

hwatari@hwatari-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink Device 0781
hwatari@hwatari-netbook:~$

---

