---
title: "ubuntu 17.10 - no wi-fi adapter found"
date: 2018-04-03
forum: Networking &amp; Wireless
---

### Post by ted67pd on 2018-04-03
Greetings,

I am relatively new to Ubuntu Linux. Installed 17.10 as a dual boot with Windows 10 in an old, but upgraded HP-6716f.

[FONT=arial]AMD Athlon ii x4 640 processor × 4
 GNOME 3.26.2,  
12 Gig/RAM, 
2 TB HD 
64 Bit OS

ASUS PCE-AC56 Wireless adapter with Broadcom 4352 Chipset
[/FONT]
Everything is working perfectly; however, **Ubuntu can't see the wireless adapter, although it knows it's there.** 

I executed: 

leo@leo-p6716f:~$ **lspci -nnk | grep -iA3 net**  

to check if secure boot might be enabled and preventing the driver from being installed.
 The OS can see both the wireless and Ethernet adapters. 

The result I get is:

leo@leo-p6716f:~$ lspci -nnk | grep -iA3 net

03:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4352 802.11ac Wireless Network Adapter [1043:85ba]
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Pavilion p6774 [103c:2ab1]
    Kernel driver in use: r8169
    Kernel modules: r8169

I can't disable secure boot from BIOS with the current version.

 Not sure if the driver installed or not. I have an Ethernet cable plugged in to the machine, so it's no big deal, but Id like to get it working right. 

Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2018-04-03
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by chili555 on 2018-04-03
The 14e4:43b1 device isn't yet included on the many guides because we're not quite sure how to get it working yet. We are happy you've volunteered to help us!

The most likely driver is bcmwl-kernel-source. Let's try:

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by ted67pd on 2018-04-03
Hello Wildmanne39.
Thank you for taking the time to look at this issue for me. Here is the link to the wireless info the script created in  pastebin:

[http://paste.ubuntu.com/p/dx7GMfnWgD/](http://paste.ubuntu.com/p/dx7GMfnWgD/)

---

### Post by wildmanne39 on 2018-04-03
It looks like chilli555 is correct as usual which is what I thought from the beginning but I wanted to make sure there was not another driver loaded that would not be taken care of by installing:
```
bcmwl-kernel-source
```
but the driver you have installed will be blacklisted when you install the other driver that chilli555 has in his post, so all should be good after that.

---

### Post by ted67pd on 2018-04-03
It worked!  
Thank you Wildmanne39 and chilli555....
All is good!

---

### Post by ted67pd on 2018-04-03
It worked!!

Thank you Chili555!!

---

