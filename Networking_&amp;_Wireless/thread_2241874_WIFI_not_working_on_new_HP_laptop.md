---
title: "WIFI not working on new HP laptop"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by Stosskraft on 2014-08-28
Hello all I just bought a new HP Pavillion 17 laptop and of course I am  trying to install Kubuntu on it. I cannot get the wifi to 'turn on' in  the menu and recognize the wifi in my house. This is a fresh install on a  brand new laptop. I know it is working because if I dual boot back to  windows 8 it automatically connects and works no problem.

I also have my HP G42 laptop running kubuntu and it is connected to the  wifi automatically with no issues. I just cant seem to get this last  hurdle solved though it must be something simple as I know the wifi is  working in the laptop and on other devices. Right now I am writing this  by plugging the wire directly inthe laptop.

Please help, I want to wipe Windows 8 from here permentaly but need wifi working first.

Thank you

---

### Post by Stosskraft on 2014-08-28
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8610G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
yanek@yanek-HP-Pavilion-17-Notebook-PC:~$ ^C
yanek@yanek-HP-Pavilion-17-Notebook-PC:~$

---

### Post by judderwocky on 2014-08-28
There are some kernel issues with the Realtek wifi drivers. They are basically, mostly, fixed in kernel 3.16.    You would need to install the updated upstream kernel which can be downloaded here:    [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)  Im guessing you want the 64 bit version...   [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb)    [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb)    [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb)  So you would install those three packages and it should work. I haven't tested 3.16.1 yet. A little curious.

---

### Post by Stosskraft on 2014-08-28
Thanks. The first link will not work 'cannot satisfy all dependancies' when trying to open the deb file. I am doing a major update right now, as it is a fresh install. Do you recommend doing the update first or the packages you suggest?

---

### Post by Stosskraft on 2014-08-29
Hello all, it seems that the update helped the wifi as now I can connect. I also installed the last 2 links you sent me, as the first one wouldn't install. Now I have an issue that the WIFI 'drops or disconnects' after a while... I think it might be VIBER that I installed, though there is no issues with Viber or WIFI on the older laptop running the same OS (Kubuntu LTS)..

Any ideas?

---

### Post by Stosskraft on 2014-08-30
bump.

---

