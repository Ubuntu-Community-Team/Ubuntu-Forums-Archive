---
title: "Broadcom based Buffalo card recognized, but not working"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by mattgif on 2007-06-28
Hi all - 
     My Atheros based Belkin wireless PCI card was performing very slowly, and doing a poor job of picking up my router's signal, so I decided to try out a new Buffalo WLI2-PCI-G54S card.  I used ndiswrapper to install the drivers with the official .inf/.sys files from the manufacturer.  

     Now in my wireless network task-manager icon (the little signal bars by the clock) it reads "Wireless Networks (Broadcom Corporation BCM4318 [AirForce one 54G] 802.11g wireless LAN controller)" but lists no networks underneath it.
     
iwconfig gives the result:


> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"<my network's silly SSID>"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:D1:1B:28   
          Bit Rate:36 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/94  Signal level=-48 dBm  Noise level=-91 dBm
          Rx invalid nwid:1608  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


There were 3 .inf files included with the driver, maybe I installed the wrong one?  I don't know; I'm very much a Linux dummy.  How can I get this card to start recognizing the plethora of networks around it?

Thanks in advance for your help, folks.  It's very kind of you to share your knowledge with blundering fools like me!

Note: The card listed as ath0 is my old card, which I left in just in case something like this happened.  Oh, and sorry for those damnable emoticons that pop up in the middle of the quoted passage; the forum decorated that for me.  I didn't want to remove the colons or change the text lest I altered something important.

---

### Post by Antonio44 on 2007-06-28
Ok I have the Broadcom 4318 in my laptop. Let me tell you it took me darn near a month and three fresh installs. But this article here worked like a charm. I don't know if this will work for you or not but try it at your own risk. Best of luck!

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)


A.

---

### Post by mattgif on 2007-06-28
Well, I have a desktop, but I suppose I'm willing (or stupid) enough to give it a shot!  I'll let you know how it turns out.

---

### Post by mattgif on 2007-06-28
Followed the instructions, but I'm not sure if those were the right drivers.  In any event, the new card doesn't even appear in iwconfig: 

> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tanglewood Adult Party!"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:D1:1B:28   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-44 dBm  Noise level=-88 dBm
          Rx invalid nwid:3661  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Darn.  Any other ideas?

---

### Post by Antonio44 on 2007-06-28
Sorry dude but thats about all I have. Did you try searching your model along with ndiswrapper in google that is all that I can think of to do. There are people out there that are more tech savvy then    me. Most are on this forum. Sorry I can't help more.

---

### Post by kevdog on 2007-06-29
Can you list the following:

lshw -C network
lspci
/etc/network/interfaces
/etc/iftab
ndiswrapper -v 
ndiswrapper -l

Sorry about the long list.

---

### Post by mattgif on 2007-07-01
Sure! 
Results of lshw -C network:
> 
*-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:01:83:c0
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=1.1-0 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:92200000-9221ffff iomemory:92224000-92224fff ioport:30c0-30df irq:20
  *-network:0 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@07:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=32
       resources: iomemory:92014000-92015fff irq:21
  *-network:1
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@07:02.0
       logical name: wifi0
       version: 01
       serial: 00:11:50:d5:05:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) ip=192.168.2.6 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g 

Results of lspci:
> 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
07:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


Results of /etc/network/interfaces

> auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto eth0

Contents of /etc/iftab:
>  # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:19:d1:01:83:c0 arp 1
ath0 mac 00:11:50:d5:05:fe arp


Results of ndiswrapper -v :
> 
utils Error: no version specified!
driver version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload


Results of ndiswrapper -l:
> utils Error: no version specified!
driver version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 
matthew@matt-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
net2pg54 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
netbwc2k : invalid driver!
netcbg54 : driver installed
netwc2k : invalid driver!


Thanks for taking the time to look over that long list, I appreciate it.

---

