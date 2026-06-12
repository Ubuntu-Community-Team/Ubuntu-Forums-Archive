---
title: "Troubleshooting: WMP54G v2 or possibly 1"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by spikee on 2007-08-30
Hi there, I have searched the forums and have not come up fully empty handed as I have seen the newer models of my wireless pci card except they are WMP54G v4 or 4.1 work with ndiswrapper. I am trying to set up either WMP54G v2 which doesn't use ralink like 4 or 4.1, but I don't know how to get the inf file. I'm pretty damn sure I installed ndiswrapper for the most part. Any help would be greatly appreciated.

---

### Post by bmartin on 2007-08-31
Check the output of **lsusb** (if it's a USB device) or **lspci** (if it's anything else) and post the relevant output here.

---

### Post by spikee on 2007-08-31
Hi there thanks for your reply. I got the following output(s) after running lspci and lshw -C network:


WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 78
       serial: 00:01:03:c4:bc:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:dc00-dc7f iomemory:ff8edc00-ff8edc7f irq:11
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@01:0a.0
       logical name: eth1
       version: 03
       serial: 00:0c:41:62:9a:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff8ee000-ff8effff irq:3
jkantro@jkantro-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:0b.0 PCI bridge: Pericom Semiconductor Unknown device 8140
02:08.0 USB Controller: NEC Corporation USB (rev 43)
02:08.1 USB Controller: NEC Corporation USB (rev 43)
02:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by spikee on 2007-08-31
Hmm sorry for the quick double post but just found out that it seems to be version 2 but obviously broadcom than ralink. It's just I can't get it to work with ndis wrapper or I'm settinng it up wrong.

---

### Post by bmartin on 2007-08-31
Try doing the following:

[LIST=1]
[*]Run **ndiswrapper -l** and look at all the installed drivers. Uninstall all of the installed wireless drivers. The command to uninstall a driver is **ndiswrapper -e (driver)**. If you've done this correctly, **ndiswrapper -l** should have an empty output.
[*]Install ndiswrapper and the Broadcom drivers using [this thread]("http://ubuntuforums.org/showthread.php?t=405990"). It'll update your version of ndiswrapper and it has the appropriate version of the Windows drivers (assuming you're using a 32-bit version of Ubuntu). All you need is a working wired connection in order to get everything up-and-running.
[/LIST]

---

### Post by spikee on 2007-09-01
Alright I'll give this a shot in the morning. Thanks so much for you help. I'll let you know how it turns out.:)

---

### Post by spikee on 2007-09-01
Well i did as you said, but it's still not working. The network i'm connecting to is not wep or wpa protected. Is there a certain way I should be setting this up or?

---

### Post by bmartin on 2007-09-02
If your card is set up properly, the **iwlist** command should give some information on the wireless device. If that's not the case, then you don't have the proper drivers installed.

If you can see the wireless device in **iwlist**, try **sudo iwlist scanning**. If you can see the device but it doesn't find any wireless networks with that command, then scanning is disabled on your device (this can be due to a switch... it might be activated by pressing something on your computer or by a keyboard combination).

If **iwlist** shows you your wireless device and **sudo iwlist scanning** displays your wireless network, then your device is ready to connect. If you're having trouble with the default network manager, try installing [WICD]("http://blakecmartin.googlepages.com/wicd.html"). If you're using an ASCII WEP key, you might have to put "double quotes" around it.

---

