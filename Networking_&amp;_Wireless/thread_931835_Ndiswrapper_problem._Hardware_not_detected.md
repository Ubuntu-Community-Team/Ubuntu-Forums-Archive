---
title: "Ndiswrapper problem. Hardware not detected?"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by lcruz007 on 2008-09-27
Hello all!
I have been lately trying to install Ndiswrapper for Ubuntu. I have successfully installed Ndiswrapper and my Wireless driver, however, when I try to see if my driver was successfully installed with the command: **Ndiswrapper -l**, I get ***netw4v32 : driver installed***, but doesn't it have to show if it detects the hardware?

If I try checking if my network is working correctly with **ifconfig**, it doesn't shows up the alias I created for the driver, "wlan0".

You can see the following screenshot:
[IMG]http://i26.photobucket.com/albums/c107/luis007cruz/Screenshot-luisluis-laptop.png[/IMG]


Someone knows what's the problem?


Thanks in advance.

---

### Post by ajmorris on 2008-09-27
hi there,
yes, if it detects the hardware, it will show a device id, and say it is present, i.e.:
> device (some device id) present

To see if your wireless card is detected, what is the output of ```
sudo lspci
```

AJ

---

### Post by lcruz007 on 2008-09-27
> **ajmorris said:**
> hi there,
yes, if it detects the hardware, it will show a device id, and say it is present, i.e.:


To see if your wireless card is detected, what is the output of ```
sudo lspci
```

AJ

I get this output:
[B]
luis@luis-laptop:~$ sudo lspci
[sudo] password for luis: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
luis@luis-laptop:~$ [/B]

---

### Post by cariboo on 2008-09-27
Could you post the output of:

```
sudo lshw -C network
```

That should show us if your wireless card is working.

Jim

---

### Post by lcruz007 on 2008-09-27
> **cariboo907 said:**
> Could you post the output of:

```
sudo lshw -C network
```

That should show us if your wireless card is working.

Jim
Output:
[B]
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:3e:dd:21
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.112 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
[/B]

---

### Post by lcruz007 on 2008-09-27
Does someone knows what's going on?

---

### Post by ajmorris on 2008-09-27
are you sure that is the correct wireless driver for the Atheros AR242x card? (AKA AR5007EG)

Also, if the restricted drivers that are provided in hardy are not functioning, make sure you disable them from System --> Administration --> Hardware Drivers.

googling dug up these drivers for that card:
[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

Also, have you tried madwifi?

AJ

---

### Post by lcruz007 on 2008-09-28
> **ajmorris said:**
> are you sure that is the correct wireless driver for the Atheros AR242x card? (AKA AR5007EG)

Also, if the restricted drivers that are provided in hardy are not functioning, make sure you disable them from System --> Administration --> Hardware Drivers.

googling dug up these drivers for that card:
[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

Also, have you tried madwifi?

AJ
Ok, thank you! finally I get this as an output:

[B]net5211 : driver installed
	device (168C:001C) present
[/B]

When I tried to make an alias, I accidentally deleted mdprobe in /usr/sbin... Do you know how can I restore it?


Thank you

---

### Post by ajmorris on 2008-09-28
[QUOTE=lcruz007]When I tried to make an alias, I accidentally deleted mdprobe in /usr/sbin... Do you know how can I restore it?[/QUOTE] ?? modprobe is in /sbin not /usr/sbin, and also it is part of the base ubuntu system, so cannot be re-installed without a re-install of ubuntu, however, as it is only a binary file, if you get someone else that is running the same base ubuntu system as you, i.e Hardy 32bit, you can just use their /sbin/modprobe file :)

I however, do not have hardy, or a 32bit system.... you could just copy the file of the live cd or other install media that you used to install ubuntu.

AJ

---

### Post by lcruz007 on 2008-09-30
Ok, I re-installed Ubuntu and reinstalled ndiswrapper with the correct driver. I don't know why it doesn't works though, wlan0 doesn't shows up.
*Outcome:*
[IMG]http://i26.photobucket.com/albums/c107/luis007cruz/Screenshot-rootluis-laptop.png[/IMG]


What's the problem?


Thanks

---

### Post by lcruz007 on 2008-09-30
bump

---

### Post by ajmorris on 2008-09-30
> **lcruz007 said:**
> Ok, I re-installed Ubuntu and reinstalled ndiswrapper with the correct driver. I don't know why it doesn't works though, wlan0 doesn't shows up.
What's the problem?

Thanks

run the following commands:
```
sudo su
```
```
rmmod ndiswrapper
```
```
ndiswrapper -a 168C:001C net5211
```
```
modprobe ndiswrapper
```

if this still doesnt work, can you post the contents of your /etc/modprobe.d/blacklist  file

AJ

---

### Post by lcruz007 on 2008-10-02
> **ajmorris said:**
> run the following commands:
```
sudo su
```
```
rmmod ndiswrapper
```
```
ndiswrapper -a 168C:001C net5211
```
```
modprobe ndiswrapper
```

if this still doesnt work, can you post the contents of your /etc/modprobe.d/blacklist  file

AJ

Didn't work, I get this:
[IMG]http://i26.photobucket.com/albums/c107/luis007cruz/Screenshot-rootluis-laptop-1.png[/IMG]

My computer gets freezed with the last command. 


How do I access the blacklist file?

[IMG]http://i26.photobucket.com/albums/c107/luis007cruz/Screenshot-luisluis-laptop-etc-modp.png[/IMG]

---

### Post by ajmorris on 2008-10-03
> **lcruz007 said:**
> 

How do I access the blacklist file?



if you are using the terminal, you have two options to edit the file, you can run a CLI editor, such as vim or nano on the file. Or open up a GUI editor, such as gedit.

AJ

---

