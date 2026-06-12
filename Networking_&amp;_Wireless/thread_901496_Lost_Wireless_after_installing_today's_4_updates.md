---
title: "Lost Wireless after installing today's 4 updates"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by cybrsaylr on 2008-08-26
Help.

My couple month old Toshiba laptop is back on a wired connection.
After installing today's 4 updates it required a PC reboot.
I reboot and lost my wireless connection.

It was running great as I used for about a half hour, prior to noticing the 'updates are available' prompt. I decided to update and install those 4 updates, then rebooted as instructed and now have no wireless. 

Anyone know what happened and can someone help me get the wireless working again as it was before?

---

### Post by Sam Lars on 2008-08-26
Could you post the output of
```
lspci | grep Network
```
and
```
iwconfig
```

---

### Post by coffeecat on 2008-08-26
> **cybrsaylr said:**
> I reboot and lost my wireless connection.

Also, please post the output of:

```
uname -r
```You haven't enabled the [Proposed updates repository]("https://help.ubuntu.com/community/UbuntuUpdates"), have you?

What version of Ubuntu are you running?

---

### Post by cybrsaylr on 2008-08-26
When twice putting in, lspci | grep Network, I got no results.

I put in, lspci, and the other two requested and got this:

tt@tt-laptop:~$ lspci | grep Network
tt@tt-laptop:~$ lspci | grep Network
tt@tt-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
tt@tt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tt@tt-laptop:~$ uname -r
2.6.24-19-generic


You haven't enabled the Proposed updates repository, have you?  

No I don't believe or recall doing that.

What version of Ubuntu are you running?

Running 8.04

---

### Post by cybrsaylr on 2008-08-26
Also I notice when clicking on Network Settings, Wireless is no longer listed. 
Only Wired connection and Point to Point connection, is listed.
Wired connection has a checkmark in front of it.

---

### Post by Sam Lars on 2008-08-26
I guess it's not seeing your card as a wireless card?
Try rebooting.  Right after your BIOS screen there will be the Grub menu, or a prompt to hit Escape to get to it.  There should be a few different versions on the kernel, try booting one that isn't the most recent number.

---

### Post by cybrsaylr on 2008-08-26
Sam Lars,

Tried doing that with another version as you suggested at startup but it didn't help.
Wireless still doesn't work.

---

### Post by AndySaunders on 2008-08-26
I've been having the same issues and followed the same steps, here's what I'm getting:

--

andy@andy-laptop:~$ lspci | grep Atheros
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
andy@andy-laptop:~$ uname -r
2.6.24-19-generic
andy@andy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Sam Lars on 2008-08-26
If no one else has suggestions you should file a bug about it.

---

### Post by cybrsaylr on 2008-08-26
Got this, lspci | grep, working now. 
It wouldn't work in terminal earlier, why I have no idea.

tt@tt-laptop:~$ lspci | grep Atheros
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
tt@tt-laptop:~$  uname -r
2.6.24-19-generic
tt@tt-laptop:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Prior to this upgrade wireless ran great.

---

### Post by cybrsaylr on 2008-08-29
Still can't get wireless working again like before and have to use a wired connection.
Tried a few of the suggestions from other threads with no luck yet.

Was hoping someone came up with a easy fix by now to enable wireless again.

---

