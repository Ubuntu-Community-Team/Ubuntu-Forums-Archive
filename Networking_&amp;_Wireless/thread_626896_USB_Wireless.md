---
title: "USB Wireless"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by jholding on 2007-11-29
Hello,

I installed Ubuntu 7.10 and the system recognizes my USB wireless adapter (lsusb: Bus 005 Device 003: ID 1286:1fab) but I can't figure out how to get it to work.

PLEASE HELP

THanks

---

### Post by JawsThemeSwimming428 on 2007-11-29
Go into Network Manager and make sure your wireless connection is set up right. What brand, model, and version wireless USB adapter is it? Also, what version of Ubuntu are you running?

---

### Post by rustybronco on 2007-11-29
Should be a marvell chipset (v1?) 
post the output of lshw -C usb  and  lshw -C network

---

### Post by jholding on 2007-12-01
Thanks for answering my post.

The model is Zonet 802.11g usb; zew2502;

I did not getting any output when I ran lshw -C usb

jholding@jholding-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:3a:f7:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.2.4 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

### Post by rustybronco on 2007-12-01
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)
> Card: Zonet ZEW2502 802.11b/g USB Adapter
Chipset: Marvell Semiconductor, Inc., Libertas 802.11 g/b Wireless
pciid: 1286:1fab
Driver: Windows XP/2K version 2.1.0.18 (inf)/1.02 (directory name) from the CD included with the device (not available for download at this time from Zonet&#8217;s support site), /mnt/cdrom/V1.02 driver and utility install(USB)/Inf/WinXP_2K/netMw225.inf
Other: ndiswrapper 1.9 / kernel 2.6.17-1.2174

The only thing I could find is a ndiswrapper install for this usb device, there is a ndiswrapper how to in my signature. [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

also  [http://ubuntuforums.org/showthread.php?t=551250](http://ubuntuforums.org/showthread.php?t=551250)

Let me know if you need help.

---

### Post by jholding on 2007-12-16
Thanks for the help although it didn't work. I suspect that my wireless device is just a piece of junk. Not too much of a surprise as it was cheap,

But thanks for the help.

---

### Post by Kasper42 on 2007-12-17
@jholding, I have previously successfully set-up my wifi usb stick with the same ID of 1286:1fab though it was branded as Dynamode not Zonet. I used the netMw225.inf and MRVW225.sys files on ndiswrapper which seemed to work okay but did experience frequent drop outs.

Anyway, I recently had a HDD failure and I had to reinstall ubuntu. I have installed ndiswrapper and the correct drivers (they worked last time on gutsy) When I run 'ndiswrapper -l' I get the message:

```

netmw225: driver installed
device (1286:1fab) present
```

Yet the LED on the USB stick does not light up and when I go to Networking or Windows Wireless Drivers (the graphical frontend for ndiswrapper) it tells me that the hardware is not present. I don't understand why in the terminal I get the message that the device is present yet in Networking or in Windows Wireless Drivers it seems my hardware is not recognised :confused:

Is this something to do with me running feisty as I do not remember the same problem on Gutsy?

Thanks for any help :)

.:EDIT:. RIght, I uninstalled the driver I installed through the terminal and reinstalled it in the graphical frontend of ndiswrapper, it still seems to think the hardware is not present but it has since loaded on the Networking options :) Hope this helps someone with a similar problem.

---

