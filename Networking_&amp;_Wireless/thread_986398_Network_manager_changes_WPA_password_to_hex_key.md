---
title: "Network manager changes WPA password to hex key?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by magical_graam on 2008-11-18
I upgraded to 8.10 recently, and I have been having some problems with the network manager. When it tries to connect, it sometimes asks for the password again, and in the box where you enter the password, it shows a really long hex string instead of the original password. I put in the right password and sometimes it works straight away, sometimes it takes a few tries. It always manages to connect eventually, but its really annoying, especially when there was no problem in Hardy.

I've searched and found other people with similar problems, but the only solution I've found is to use wicd, which doesn't connect at all on mine :(

I have a Broadcom 4312 wireless card and I'm using ndiswrapper for the driver

---

### Post by magical_graam on 2008-11-22
bump

---

### Post by LodeRunner on 2009-01-22
Same problem, except I cannot get it to work at all. I briefly had a workaround whereby Kwallet was managing my keys (while still using Gnome), but I've since done a clean reinstall and have been unable to duplicate it.

---

### Post by wild-one on 2009-01-22
Just upgraded from Hardy to 8.1.   I never had any WiFi issues previously, but I'm running into a similar problem now.   It takes my password keystrokes correctly in the field, but the connect key is gray-ed out leaving me only with the option to cancel out and go find some Cat5.

What gives?   What changed in 8.1 from a previously stable wifi connect?:(

---

### Post by magical_graam on 2009-01-23
Wow this is an old thread :p

Well since I last posted, wicd decided to work (no idea why it didnt before. I think I just had to restart or something). I recommend you use it instead of the network manager since it is easier to use, better looking (my opinion, I'm sure others will disagree) and I havnt had any issues with it. Link: [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by jsternberg on 2009-01-23
Similar problem with WEP - my wireless also stopped working recently, although I didn't change anything (except automatic upgrades). Running 8.04 with Verizon DSL and a Westell modem, my other windows computer connects to wireless ok, so I know it's not a router problem. My Ubuntu machine sees various wireless networks, including mine, but keeps asking for hex password (although router uses WEP 138 passphrase in plain text). I see folks using Intrepid are having similar problems, but I haven't seen a fix yet, and don't know enough Linux myself. Any clues appreciated.

Ubuntu 8.04 (hardy)
2.6.24-23-generic (#1 SMP Thu Nov 27 18:44:42 UTC 2008)

i'm currently online using my ethernet connection because wireless isn't working]
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wmaster0
version: 02
serial: 00:1c:bf:36:2b:c4
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
*-network
description: Ethernet interface
product: NetLink BCM5906M Fast Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:1d:09:3a:ff:1e
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.46 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
jsternberg is online now Report Post   	Edit/Delete Message

 iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:0F:36:F0   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

