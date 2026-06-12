---
title: "Can't connect to my atheros wireless"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by phroe on 2008-10-29
Hello everyone,

I am very new to linux OS, and I have just installed Ubuntu.

my pc picked up my wifi and said it is enabled, but why isnt it connecting to the internet??? please help me, i have tried downloading all kinds of "things" and nothing was working, thats when i rebooted it. so right now my pc is fresh with ubuntu and no installs of anykind, where do i go from here

below is my info:
1st) i typed this: sudo lshw -C network and got this----->

  *-network DISABLED      
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:36:f5:9e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
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
phroe@phroes-bitch:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
__________________________________________________________________

2nd) i did this after also: sudo lspci -v and got --->

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 505
	I/O ports at 3000 [size=256]
	Memory at f4000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at cc000000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 042a
	Flags: fast devsel, IRQ 18
	Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>






Thank you to everyone....I am ill-iterate when it comes to this, i just xfred from Vista...but I want to learn!!!!!!

phroe

---

### Post by nhasian on 2008-10-29
i just answered the same question in this thread:

[http://ubuntuforums.org/showthread.php?p=6059353#post6059353](http://ubuntuforums.org/showthread.php?p=6059353#post6059353)

---

### Post by phroe on 2008-10-31
still cant connect, but it picks this up, do i now enter all the info from the wireless??

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by nhasian on 2008-11-01
yes if your wireless adaptor was detected now you can just select a wireless network from the wifi icon next to the clock in the top right of the screen.  if you are connecting to a secure network WEP or WPA then you will need the passphrase.  the DHCP server (like a wifi router or dsl/cable modem) should provide the rest of the ip settings for your computer.

---

