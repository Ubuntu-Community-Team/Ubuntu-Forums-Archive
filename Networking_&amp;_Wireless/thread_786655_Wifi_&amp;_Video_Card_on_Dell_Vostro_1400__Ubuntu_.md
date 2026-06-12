---
title: "Wifi &amp; Video Card on Dell Vostro 1400 / Ubuntu Hardy 64 bits"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Malawi on 2008-05-08
Hello,

I have a problem with my very new computer, I do not have the wifi (card not detedted, a Broadcom Bcm43xx, 4310 I think). I have install fwcutter and b43-fwcutter by hand, but it does not change anything. I also have test under Backtrack (2 and 3 Beta). It is not detedted neither.

Moreover, my video chart (Intel® Graphics Media Accelerator X3100) does not seem to be detedted neither (with Hardware Drivers/Properties). The screen works well, but when I connect the PC on a TV, there is nothing on the TV screen (even with Fn+F4).

Where do these problems come from? I do not find the solution. If somebody met this problem, thank you to answer me...

---

### Post by Ayuthia on 2008-05-08
> **Malawi said:**
> Hello,

I have a problem with my very new computer, I do not have the wifi (card not detedted, a Broadcom Bcm43xx, 4310 I think). I have install fwcutter and b43-fwcutter by hand, but it does not change anything. I also have test under Backtrack (2 and 3 Beta). It is not detedted neither.

Moreover, my video chart (Intel® Graphics Media Accelerator X3100) does not seem to be detedted neither (with Hardware Drivers/Properties). The screen works well, but when I connect the PC on a TV, there is nothing on the TV screen (even with Fn+F4).

Where do these problems come from? I do not find the solution. If somebody met this problem, thank you to answer me...
Do you have a wired connection in Ubuntu?  If so, can you post the results of lspci -nn, ifconfig, iwconfig, and iwlist scan?

As for your PC to TV, I am not familiar with configuring an Intel graphics card.  It looks like you might have to make changes on your /etc/X11/xorg.conf file.  The following link is an example on how the file might look like but won't be 100% in your case because you have a different model card: [http://ubuntuforums.org/archive/index.php/t-614821.html](http://ubuntuforums.org/archive/index.php/t-614821.html)

---

### Post by Malawi on 2008-05-08
this is the answers to the commands:

```

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

```
So as I told, my card is a Broadcom Corporation BCM4310 (rev 01)

```

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:03:67:31  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe03:6731/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2095987 (1.9 MB)  TX bytes:380521 (371.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178100 (173.9 KB)  TX bytes:178100 (173.9 KB)

```
... but is not detected

and so the other commands are useless:
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```

~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by Ayuthia on 2008-05-08
Thanks.  I needed to see the [14e4:4315] portion.  Mainly so that I can keep track of which cards are working with Ubuntu.

Can you post your lshw -C network?  It will provide information about what driver it is using, if it is still unclaimed, or is missing. 

I have not heard much about this card yet.  I have seen one user that was successful in getting it working with NDISwrapper.  Here is the link: [http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

If you do go with that option, can you still post your lshw -C network info?  I am very much interested in seeing if this will work with the b43 driver.

---

### Post by Malawi on 2008-05-08
This is the answer:

```

# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:03:67:31
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```

I will try NDISwrapper later and will tell you if there are news.
Thank you for your help,

---

### Post by Malawi on 2008-05-08
I have done the installation of NDISwrapper, but still no Wifi.
This is the answer of lshw -C network (a little bit different now).

```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:03:67:31
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.1.2 latency=0 module=tg3 multicast=yes

```

---

### Post by Ayuthia on 2008-05-08
Can you post the information on:
```
ndiswrapper -v
ndiswrapper -l
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ndiswrapper
cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
```
The first command will tell you if a working version is installed (should also be 1.50 or higher).

The second command checks to see if your driver is installed correctly.  It should have something like:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)
The device (14E4:4315 present is what we are looking for.

The third command is verifying that ndiswrapper is there so that it will load up when you reboot.

The fourth command checks to see if bcm43xx, b43, and ssb are blacklisted.  If b43 and ssb are not, there needs to be a script that will remove them before ndiswrapper is loaded.

The fifth command is checking to see that only ndiswrapper is loaded and that b43, bcm43xx, and ssb are not.

---

### Post by Malawi on 2008-05-09
```
~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-17-generic SMP mod_unload 

```

```
~$~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present

```

```
~$ cat /etc/modules|grep -i -e bcm43xx -e b43 -e ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper

```

```
~$ cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist ssb

```

```
~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
ssb                    37252  1 b44
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,uhci_hcd,ehci_hcd

```
... so changes are not saved when I reboot. 

Without rebooting , it seems to work:
```

~$ sudo modprobe -r b44
~$ sudo modprobe -r ssb
~$ sudo modprobe -r ndiswrapper
~$ sudo depmod -a
~$ sudo modprobe ndiswrapper

~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,uhci_hcd

```

What script should I write?

---

### Post by salvador_luna on 2008-05-09
check this thread:

[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

I used it and worked perfect with my Broadcom BCM94311MCG wlan mini-PCI.

Also note that i used the driver provided by hp because i have a compaq presario laptop. You should use the driver provided by dell.

Sorry about my english.

---

### Post by Ayuthia on 2008-05-09
salvador_luna's post will work.  I prefer version 0.3 from this site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c)

The reason why I say this is because it keeps the script with ndiswrapper.  So if you ever decide to switch back to b43 when the driver works better, it will be there will be less things to change.  The other option requires a couple of steps to remove.  If you happen to ask for help later to switch back, it will be more difficult to find because it is not a common file with a ndiswrapper label on it.

Were you able to connect to a site?

---

### Post by salvador_luna on 2008-05-11
Ayuthia:

Thanks for your post!

It's seems that is a much easy and clean way to make it work. I´ll try it when i had a chance.

Again, thank you!

---

