---
title: "Cant connect to Wireless - completely new to Ubuntu"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by djurornic on 2011-05-05
Hi, 

I'm sure this is posted elsewhere so my apologies in advance if there is any duplication. I have a Dell Studio 1737 running Windows 7 and I have installed 11.04 for the first time ever on my laptop. I've never used Ubuntu at all. The problem I have is that I cant enable my wireless and I have been through Ubuntu help with the following results from the command prompt window:

  *-network DISABLED
         description: Wireless interface
         physical id: 4
         logical name: wlan0
         serial: 00:23:4e:b6:f7:30
         capabilities: ethernet physical wireless
         configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
  djuroirena@ubuntu:~$ sudo lshw -C network
  

Any help on what I need to do?

Look forward to receiving your replies

Djuro

---

### Post by ubudog on 2011-05-05
First of all, welcome to Ubuntu!

Type the following into a terminal, and post the output here.  

```
ifconfig
```
(this command shows your network interfaces)

Also, this would be useful information.
```
lspci
```

Have you looked in System>Administration>Additional Drivers to see if there are any drivers for your wireless card?

Good luck!

---

### Post by djurornic on 2011-05-05
Hi there....have run those commands and details as follows:

 eth0      Link encap:Ethernet  HWaddr 00:21:70:90:a8:a7  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:17
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:148 errors:0 dropped:0 overruns:0 frame:0
            TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:11440 (11.4 KB)  TX bytes:11440 (11.4 KB)
   
  and
   
  00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
  00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
  00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
  00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
  00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
  00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
  00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
  00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
  00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
  00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
  00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
  00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
  00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
  00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
  00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
  00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
  00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
  00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
  01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
  01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
  04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
  08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
  09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
  
Also triued system settings and additional drivers but there were none available and / or was not able to connect to the internet!

Also, when i click in the top right corner on the wireless icon it says "device not ready - firmware missing".

Thanks for your help so far

best, 

Djuro

---

### Post by ubudog on 2011-05-05
Try typing this:

```
sudo ifconfig wlan0 up
```

And maybe take a look at this guide... it came from another thread with the same issue you have.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by ubudog on 2011-05-05
Ok, I think I may have found something better:

[http://ubuntuforums.org/showthread.php?t=1737629](http://ubuntuforums.org/showthread.php?t=1737629)

---

### Post by computerandu on 2011-05-05
Hi,

Was wireless connected when you were installing Ubuntu 11.04?

Did it ask you to download additional driver Broadcom STA?

Its a very common problem with Broadcom network adapter. 

Here is what you need to do. Use other  Broadcom drivers. Download these drivers (from Windows or through wired  network or a friend’s computer or from wherever you are reading this  article [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1300809663g[/IMG]  ). Install these instead of the one provided by Ubuntu 11.04. For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
 For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)
 Now remove the previous drivers using: *sudo apt-get remove bcmwl-kernel-source*
 Now install the appropriate driver.  Restart your computer. If restarting doesn’t work try shut down and then  start it (strange…but works). Enjoy [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1300809663g[/IMG]




I wrote it on my blog as well....

Source: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by djurornic on 2011-05-05
Hi there, 

Thanks for your posts. I've tried your sudo command and I get the following answer:

djuroirena@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for djuroirena: 
SIOCSIFFLAGS: No such file or directory

Is that correct?

Also, I've hooked up my HTC android phone via USB to my laptop and I now have internet connection. However, I still dont have wireless :-)

When I click on the wireless icon in the top right i can see the following information:

Wired Network (Broadcom Netlink BCM5784M Gigabit Ethernet PCIe
disconnected

So how do I connect?

Look forward to receiving your replies

Djuro

---

### Post by djurornic on 2011-05-05
..........all sorted now....with my htc wired link i checked additional drivers and it has downloaded the driver for Broadcom....now surfing wirelessly with Ubuntu...love it!

---

### Post by ubudog on 2011-05-05
Yep, I knew it was a driver issue.  Glad you got it working!  PM me if you need any more help.  :-)

---

