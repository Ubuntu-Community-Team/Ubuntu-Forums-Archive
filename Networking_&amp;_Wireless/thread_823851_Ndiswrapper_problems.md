---
title: "Ndiswrapper problems"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Xanaklusmos on 2008-06-09
I did a command line only install of debian with the laptop set of packages also. I have ndiswrapper installed and the appropriate driver. The wireless does not work, I have no internet, and the computer is very old. I'm also new to Linux. Where do i go from here?

---

### Post by Ayuthia on 2008-06-09
> **Xanaklusmos said:**
> I did a command line only install of debian with the laptop set of packages also. I have ndiswrapper installed and the appropriate driver. The wireless does not work, I have no internet, and the computer is very old. I'm also new to Linux. Where do i go from here?
We need some information from you about your wireless, ndiswrapper, and kernel version.  Can you go into your computer and try to post the results of the following from the Terminal:
```
lspci -nn
ndiswrapper -v
ndiswrapper -l
uname -r
```
The first command will provide your PCI card information.  Look for Network Controller or Ethernet controller.  The second command will give the NDISwrapper version, the third provides the driver information for NDISwrapper.  The last one will provide the kernel information.

We need to determine what needs to be blacklisted or installed to help make your card work.

---

### Post by Xanaklusmos on 2008-06-18
00:00.0 Host bridge [0600]: Toshiba America Info Systems CPU to PCI bridge [1179:0601] (rev a2)
00:07.0 Communication controller [0780]: Agere Systems 56k WinModem [11c1:0441] (rev a1)
00:08.0 VGA compatible controller [0300]: S3 Inc. ViRGE/MX [5333:8c01] (rev 06)
00:0b.0 USB controller [0c03]: NEC Corporation USB [1033:0035] (rev 02)
00:10.0 IDE interface [0101]: Toshiba America Info Systems Extended IDE Controller [1179:0102] (rev 34)
00:11.0 Communication controller [0780]: Toshiba America Info Systems FIR port [1179:0701] (rev 23)
00:13.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC97 [1179:060f] (rev 07)
00:13.1 CardBus bridge [0607]: Toshiba America Info Systems ToPIC97 [1179:060f] (rev 07)
05:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]

This came up with the lspci -nn

btw, sorry this took so long I've been out of town the past week.

---

### Post by Ayuthia on 2008-06-18
> **Xanaklusmos said:**
> 
05:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]

Ok.  I am not for sure which kernel you are using, can you post the uname -r info also?

You should also check ndiswrapper -l.  Does it show that the device is present or does it only say driver installed?  If it does say that device is present, does it also show an alternate driver?  The alternate driver means that it knows that there is another driver that might work.  It could also create a conflict.  From what I am reading it looks like you might have one (acx).  To see if that module is active type:
```
lsmod |grep acx
```

---

### Post by Xanaklusmos on 2008-06-18
the uname -r has:
2.6.22-3-486

for ndiswrapper -l:
lstinds : driver installed
        device (104C:9066) present

when i do lsmod |grep acx it does nothing

---

