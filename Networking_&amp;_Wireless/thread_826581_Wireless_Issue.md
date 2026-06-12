---
title: "Wireless Issue"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Eureka89 on 2008-06-12
Hello all,
I'm new here. Just installed Ubuntu 8.04 today. Dual-booting with Vista. I just have one issue: my wireless card doesn't seem to work. I don't think Ubuntu even recognizes it. I'm using a Dell Inspiron 1520 and the wireless card came pre-installed so I'm guessing it's from Dell.

I've read other messages here, so here's what I get after typing lspci in my terminal:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

Thanks in advance,
Eureka

---

### Post by Dark_Stang on 2008-06-12
That last line is your wireless card.
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Here is a guide for you.
[http://ubuntuforums.org/showthread.php?t=766946](http://ubuntuforums.org/showthread.php?t=766946)

---

### Post by lisati on 2008-06-12
I spotted a wireless card at the bottom of the list - the line which mentions "Broadcom" and "801.11"

If you post the output of ```
iwconfig
``` and ```
iwlist scan
``` we might be able to help

---

### Post by Eureka89 on 2008-06-12
> **Dark_Stang said:**
> That last line is your wireless card.
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Here is a guide for you.
[http://ubuntuforums.org/showthread.php?t=766946](http://ubuntuforums.org/showthread.php?t=766946)
Thanks. I tried that but when I get to this line:
```
wget http://ftp.us.dell.com/network/R151517.EXE
```

I get this error:
```

--02:28:18--  http://ftp.us.dell.com/network/R151517.EXE
           => `R151517.EXE'
Resolving ftp.us.dell.com... 143.166.170.10
Connecting to ftp.us.dell.com|143.166.170.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54,750,848 (52M) [application/octet-stream]
R151517.EXE: Permission denied

Cannot write to `R151517.EXE' (Permission denied).

```

I don't know why.

> **lisati said:**
> I spotted a wireless card at the bottom of the list - the line which mentions "Broadcom" and "801.11"

If you post the output of ```
iwconfig
``` and ```
iwlist scan
``` we might be able to help
Thanks for your post.

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

**iwlist**
```

 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

There. ^_^

---

### Post by daRealScanMan on 2008-06-12
You could just download the driver from here:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R151517&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R151517&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136)

Put it somewhere on your ubuntu filesystem and continue with the instructions.

---

### Post by Ayuthia on 2008-06-12
> **Eureka89 said:**
> Thanks. I tried that but when I get to this line:
```
wget http://ftp.us.dell.com/network/R151517.EXE
```

I get this error:
```

--02:28:18--  http://ftp.us.dell.com/network/R151517.EXE
           => `R151517.EXE'
Resolving ftp.us.dell.com... 143.166.170.10
Connecting to ftp.us.dell.com|143.166.170.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54,750,848 (52M) [application/octet-stream]
R151517.EXE: Permission denied

Cannot write to `R151517.EXE' (Permission denied).

```

It looks like you are in a directory that does not allow writing without sudo privilege.  You might try creating a folder in your home directory and try downloading again.  Or else you can open up Firefox and go to [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE) and it will download it for you.

---

### Post by Eureka89 on 2008-06-12
Thanks all.

I've gotten to step three of this manual:
```
http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328
```

Problem is whenever I do this line:
```
sudo make uninstall
```

I get this:
```
make: *** No rule to make target `uninstall'.  Stop.
```

:(

What now?

Thanks again.

---

### Post by Ayuthia on 2008-06-12
> **Eureka89 said:**
> Thanks all.

I've gotten to step three of this manual:
```
http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328
```

Problem is whenever I do this line:
```
sudo make uninstall
```

I get this:
```
make: *** No rule to make target `uninstall'.  Stop.
```

:(

What now?

Thanks again.

I think that you are in the wrong directory.  Did you change to the ndiswrapper directory:
```
cd ndiswrapper-1.5*
```
If so, can you post the results of:
```
ls
```

---

### Post by Eureka89 on 2008-06-12
> **Ayuthia said:**
> I think that you are in the wrong directory.  Did you change to the ndiswrapper directory:
```
cd ndiswrapper-1.5*
```
If so, can you post the results of:
```
ls
```
Thanks so much. You were right. I got everything working fine now. My wireless is working. Thanks all!

---

