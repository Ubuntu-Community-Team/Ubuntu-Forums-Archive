---
title: "What did I do?! (Wireless network driver)"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by kextyn on 2008-03-31
I was installing a USB wireless adapter on a Thinkpad T43 and managed to royally screw something up.  I followed the instructions [here]("http://aircrack-ng.org/doku.php?id=r8187") to patch the driver (I did the Ubuntu 7.10 steps near the bottom before doing anything at the top.)  I know this should work, at least on some systems, because I did the same thing on a desktop and had no issues.  What happened after I restarted the laptop is my mini-pci wireless card no longer appeared.  I also couldn't get the USB adapter to go into monitor mode nor could I connect to any networks (although I didn't try connecting untill after I messed with a couple iwconfig settings which I believe I set back to the defaults.)  When I click on the network icon to connect to a wireless network it shows me the list but has no signal strength for any of them.  Please help.

Here are some things to check out:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:10:C6:CD:0B:AE  
          inet addr:10.0.0.54  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33392 (32.6 KB)  TX bytes:33392 (32.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:CA:1A:66:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:6 dropped:304 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4346 (4.2 KB)  TX bytes:576 (576.0 b)

```

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:10:C6:CD:0B:AE  
          inet addr:10.0.0.54  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33392 (32.6 KB)  TX bytes:33392 (32.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:CA:1A:66:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:6 dropped:318 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4346 (4.2 KB)  TX bytes:576 (576.0 b)

```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback





iface eth0 inet static
address 10.0.0.54
netmask 255.255.255.0
gateway 10.0.0.1

auto eth0

```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
```

Wlan0 is my USB adapter and my mini-pci adapter was Eth1.

---

### Post by kextyn on 2008-04-01
Ok, it's actually not as bad as I thought.  I can connect to a network as long as it's WEP (I think I have to recompile the driver for WPA.)  But I still can't see the signal strength of the networks.  I also can not go back into monitor mode after connecting to a network.  And of course I still only have the USB adapter showing up.

---

