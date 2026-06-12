---
title: "Network Manager and Wireless Connection Issues"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by mattshiloh on 2009-09-05
Ok, my name is Matt, long time reader, first time cal... err, wrong format.

Uhm, yeah so I am having an issue with Ubuntu that I am perplexed on and I need some help from the resident gurus to explain something to me.

I've been running Ubuntu for a few months now, and am learning the ins and outs, but I am having a rather frustrating issue in that randomly my Network Manager will stop and I will get the message "Network Manager is not running" necessitating a reboot in order to get back online.  Any ideas on this?

Next issue might be related. I use a Cricket Broadband device to connect (yeah, Cricket doesn't support it and I actually got bad mouthed by a Cricket Technical Support Supervisor for running a "substandard" operating system.  I didn't feel like explaining that Ubuntu really isn't an OS and all that jazz.)  Anyhow, there are times I want to connect with my internal wireless card, yet it never sems to connect.  The drivers appear to be loaded, and I do see see wireless networks that are available, but I never can connect to them.  I attempt to connect to unsecured ones (like public wifi, coffee shops, etc) and nothing.  Any ideas on this one?

I am running Ubuntu 9.04 on a Dell Inspiron 1501.  I don't know how to do the cool system information stuff to give you more specs from Ubuntu yet like you can wiht dxdiag on a Windows machine, so if you need more info, let me know how to generate the report and I will post it.

Thanks in advance.

Respectfully,
Matthew Jackson

---

### Post by Liolikas on 2009-09-05
I can explain "hard" CLI way. :popcorn:

sudo iwconfig
Will show what wireless capable cards with drivers you have. eth0, eth1, wlan0 etc. we will call card_name.
sudo iwlist scan
is simple network scanner, shows wireless networks names list.
sudo iwconfig card_name essid network_name
Connects card to network.
dhclient card_name
Asks for IP address from network router.
ping google.com
Way to check if everything is OK. ctrl+c to stop it.

I actually use it and problem never. If we talk about wired things so just IP asking is required.

If you still have problems ask more. Better post output of:
**lspci**
As standardized hardware information.

---

### Post by mattshiloh on 2009-09-05
Thanks for the instructions on the hardware output.  I have generated that output and am posting it below:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
root@Scotch:~# 

It seems to be misrepresenting my Radeon Xpress card, since it is not a 200M, but an 1150 instead.  Not sure this matters a heck of a lot other than recognizing the video memory, which might explain why I have never been able to get the 3D render for Compiz to work right.  Of course AMD and ATI aren't appearantly well known for proving good drivers, not like NVidia anyhow.

---

### Post by jnorthr on 2009-09-05
This line means you have the hardware:

05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

which is a device capable of quite good transmission rates. Now if we look at the messages that result when you first boot your system, we can gain further clues as to whats going on.

Find menu item System >Admin>Log File Viewer (os similar) and find the syslog choice. There are the log messages the o/s generates on start up. Scroll to the bottom to see the most recent messages.
Now scroll back up the messages until you find one with todays date and a time that seems to be about the time of your most recent bootup.

From there you can see messages, time-wise, from the moment your system begins a bootup.

Now look for any message related to wireless or wlan0 or eth0 or BCM4312, etc. This will provide further clues. Hang in there :)

---

### Post by michaelkiss on 2009-09-15
Hello, I seem to have the same problem. Yesterday (2009-09-14) i had to reboot after an update. Since then, i can't seem to connect wirelessly.
'Enable Wireless' is ticked in when clicking on the Network Manager pictogram, but no networks are offered.

I have a Dell Studio 15 and the wireless card is BCM4312

This is the lspci output

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
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
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

I can't seem to find to find "BCM4312" in syslog, however i did find a reference to "BCM4315"

```
Sep 15 00:07:56 michael-laptop kernel: [   11.406355] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
```

Which might be strange, since it should be 4312 (??)

Maybe the following is of value to solve the problem?
More extracts from syslog;

```
Sep 15 00:07:59 michael-laptop ntpd[2703]: bind() fd 20, family 10, port 123, scope 3, addr fe80::222:5fff:fea8:943b, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Sep 15 00:07:59 michael-laptop ntpd[2703]: unable to create socket on eth1 (4) for fe80::222:5fff:fea8:943b#123
Sep 15 00:07:59 michael-laptop ntpd[2703]: failed to initialize interface for address fe80::222:5fff:fea8:943b
Sep 15 00:08:00 michael-laptop NetworkManager: <info>  (eth1): driver does not support SSID scans (scan_capa 0x00). 
Sep 15 00:08:00 michael-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl') 
Sep 15 00:08:00 michael-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_22_5f_a8_94_3b 
Sep 15 00:08:00 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_19_f4_63_92, iface: eth0): not well known
Sep 15 00:08:00 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_5f_a8_94_3b, iface: eth1): not well known
Sep 15 00:08:01 michael-laptop NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle 
Sep 15 00:08:05 michael-laptop NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Sep 15 00:08:05 michael-laptop NetworkManager: <info>  (eth1): preparing device. 
Sep 15 00:08:05 michael-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Sep 15 00:08:05 michael-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Sep 15 00:08:05 michael-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Sep 15 00:08:05 michael-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready 
```

Could somebody please advise at his or her earliest convenience?

Thank you, Michaël

---

### Post by nothingspecial on 2009-09-15
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1215137.html") thread.

---

### Post by michaelkiss on 2009-09-15
Thanks, I checked that page, and it's not due to blacklist.conf

Could it be that the wireless card is broken? i really don't want to install vista just to find out whether or not it works on windows :(

---

### Post by pbrane on 2009-09-15
Where did you get the Broadcom Corporation BCM4312 802.11a/b/g (rev 01) driver? Some Broadcom wireless drivers don't come with the Linux kernel. You may need to download one from Broadcom. They (finally) released a Linux driver. If you are using the bcm43xx driver the 4312 should be supported but only for 802.11 b/g. You can have a look at this link [http://bcm43xx.berlios.de/?go=documentation]("http://bcm43xx.berlios.de/?go=documentation") or search the Ubuntu forums for wireless driver support.

As for the Cricket USB device I am not aware of any support for Linux. There are topics on Ubuntu forums about this. Also if you are running an Ubuntu OS it is not "substandard". On the contrary... Cricket would be wise to bring their drivers up to "standard" and write one for the Linux kernel. It seems that the worst OS on the planet gets the most publicity (and drivers).

Here is a supported device list for the bcm43xx driver:
[http://bcm43xx.berlios.de/?go=devices]("http://bcm43xx.berlios.de/?go=devices")

---

### Post by bkratz on 2009-09-15
> **michaelkiss said:**
> Hello, I seem to have the same problem. Yesterday (2009-09-14) i had to reboot after an update. Since then, i can't seem to connect wirelessly.
'Enable Wireless' is ticked in when clicking on the Network Manager pictogram, but no networks are offered.

I have a Dell Studio 15 and the wireless card is BCM4312

This is the lspci output
.
.
.

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
.
.
.

Which might be strange, since it should be 4312 (??)

Maybe the following is of value to solve the problem?
More extracts from syslog;


Could somebody please advise at his or her earliest convenience?

Thank you, Michaël




This might be interesting for you.

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

Good Luck

---

### Post by michaelkiss on 2009-09-15
thanks guys for answering so promptly.
I have tried quite a few proposed solutions, however none seem to work.
I'll just have to live without wifi ;)

---

### Post by michaelkiss on 2009-09-15
Guys, it's working again.
Don't ask my how please :-)

But i'm happy it works again.
All you guys offering solutions --> Big Thanks!

---

### Post by zjunkie on 2009-10-29
I just ran into the same problem on my new Inspiron 1545. Turns out that my particular model converted the function keys to hardware keys (f2 is the hotkey for enabling/disabling wireless) So when I went to open a konsole (using alt+f2) I accidentally turned off my wifi. you may want to make sure that yours is on. (and go into the bios and set the function keys so they are function keys :) )

---

