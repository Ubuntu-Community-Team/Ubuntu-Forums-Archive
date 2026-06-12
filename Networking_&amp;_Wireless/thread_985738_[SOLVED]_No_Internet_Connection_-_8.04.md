---
title: "[SOLVED] No Internet Connection - 8.04"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by CX15 on 2008-11-17
Hi everyone
(Ubuntu newbie, so be gentle please)

Just installed Ubuntu 8.04, but there is no connection to the internet.
The two small computers on the top bar has a orange exclamation mark with them and showss "No network connection" if I hover th mouse over them.

My PC has onboard LAN (Asus P5QL-PRO Motherbrd). This is hardwired to a DSL router.

Could someone steer me in the right direction of solving this.
I just pent an hour searching and reading old posts. Most of them I dont understand or it's about wireless.

Thanx in advance
CX

---

### Post by pytheas22 on 2008-11-17
Almost every ethernet card in the world should 'just work' in Linux, but sometimes there are bugs that prevent this.

The first thing to try is turning off your computer completely (i.e. not just suspend or hibernate), then unplug the power cord (and if it's a laptop, unplug the battery too).  Wait a minute, then plug the cords back in and reboot the computer.  This will force your ethernet card to reset itself, which solves some problems caused by Windows.

If that doesn't help, please open a terminal by going to Applications>Accessories>Terminal, then run the following commands (one per line; remember that case matters in Linux so capital letters must be capital):
```

lspci -nn
lshw -C Network
dmesg | grep -e 8139 -e rtl -e eth
```

Then copy the output by highlighting it, right-clicking and selecting 'copy'.  Next, paste it into a text file (which you can open from Applications>Accessories>Text Editor).  Save this text file to a USB drive or CD and transfer it to a computer that has Internet access so that you can paste the contents of the file here.  With that information we can figure out what's wrong.

---

### Post by CX15 on 2008-11-18
Thanx for the reply

> The first thing to try is turning off your computer completely (i.e. not just suspend or hibernate), then unplug the power cord (and if it's a laptop, unplug the battery too). Wait a minute, then plug the cords back in and reboot the computer. This will force your ethernet card to reset itself, which solves some problems caused by Windows.

No luck with this :(

> If that doesn't help, please open a terminal by going to Applications>Accessories>Terminal, then run the following commands (one per line; remember that case matters in Linux so capital letters must be capital):
Code:

lspci -nn
lshw -C Network
dmesg | grep -e 8139 -e rtl -e eth




Here is the output:
> 
lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Eaglelake DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Eaglelake PCI Express Root Port [8086:2e21] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation ICH10 USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation ICH10 HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 1 [8086:3a40]
00:1c.4 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation ICH10 USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH10 LPC Interface Controller [8086:3a18]
00:1f.2 SATA controller [0106]: Intel Corporation ICH10 6 port SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation ICH10 SMBus Controller [8086:3a30]
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0605] (rev a2)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Unknown device [1969:1026] (rev b0)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev b2)



lshw -C Network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


  
dmesg | grep -e 8139 -e rtl -e eth

[   34.483275] Driver 'sd' needs updating - please use bus_type methods



Hope it helps...

---

### Post by pytheas22 on 2008-11-18
What is the output of these commands:
```

sudo modprobe -r atl1 atl1e atl2
sudo modprobe atl1e MediaType=1
dmesg | tail
sudo dhclient eth0
```

Are you online now?  If not, please try (and post the output of):
```

sudo modprobe -r atl1 atl1e atl2
sudo modprobe atl1
dmesg | tail
sudo dhclient eth0
```

There's also a thread [here]("http://ubuntuforums.org/showthread.php?t=770173&page=1") that you may want to look at regarding this card.  See post 7 in particular, which explains how to manually compile a driver--but try running the commands above first, as they should get you online with the need to install any driver.

I have to sleep but will be back tomorrow.

Also, this card should work out-of-the-box in Ubuntu 8.10 (according to what I'm reading online), so you may want to consider upgrading to that.

---

### Post by CX15 on 2008-11-18
Still not working after these commands:

> sudo modprobe -r atl1 atl1e atl2
sudo modprobe atl1e MediaType=1
dmesg | tail
sudo dhclient eth0

Here is the output you asked for:

> 
sudo modprobe -r atl1 atl1e atl2

[sudo] password for xxxx: 
FATAL: Module atl1e not found.



sudo modprobe atl1

--no output at all for this one--



dmesg | tail
[   70.312418] sd 9:0:0:0: [sdf] Write Protect is off
[   70.312420] sd 9:0:0:0: [sdf] Mode Sense: 43 00 00 00
[   70.312421] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[   70.315163] sd 9:0:0:0: [sdf] 252928 512-byte hardware sectors (129 MB)
[   70.316285] sd 9:0:0:0: [sdf] Write Protect is off
[   70.316287] sd 9:0:0:0: [sdf] Mode Sense: 43 00 00 00
[   70.316288] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[   70.316290]  sdf: sdf1
[   70.361760] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[   70.361786] sd 9:0:0:0: Attached scsi generic sg5 type 0



sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device



I will try the instructions for installing the driver.
Maybe that will work.

Thanks so far
CX

---

### Post by CX15 on 2008-11-18
Success!!

Thankyou very much - Internet now working!:lolflag:

---

