---
title: "BCM 4306 on but cant see networks"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by IronFox on 2008-11-25
Ive got the Broadcom 4306 wireless card and using the b43 driver with the "hardware drivers" tool using fwcutter.  The wireless light is on, the network manager sees the card, everything sees the card as well but can not find any networks encrypted or not.  When I manually tried to connect to a wireless netowrk, ifconfig showed that I was sending packets.  What gives?

Post for ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a2:1f:f2  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea2:1ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10306150 (10.3 MB)  TX bytes:463234 (463.2 KB)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:ea:ec:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-EA-EC-09-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**

```

lspci -n
```
00:00.0 0600: 8086:2580 (rev 0e)
00:01.0 0604: 8086:2581 (rev 0e)
00:1c.0 0604: 8086:2660 (rev 03)
00:1d.0 0c03: 8086:2658 (rev 03)
00:1d.1 0c03: 8086:2659 (rev 03)
00:1d.2 0c03: 8086:265a (rev 03)
00:1d.3 0c03: 8086:265b (rev 03)
00:1d.7 0c03: 8086:265c (rev 03)
00:1e.0 0604: 8086:244e (rev d3)
00:1e.2 0401: 8086:266e (rev 03)
00:1e.3 0703: 8086:266d (rev 03)
00:1f.0 0601: 8086:2640 (rev 03)
00:1f.1 0101: 8086:266f (rev 03)
00:1f.3 0c05: 8086:266a (rev 03)
01:00.0 0300: 1002:5460
0b:00.0 0607: 104c:8031
0b:00.2 0c00: 104c:8032
0b:00.3 0180: 104c:8033
0b:00.4 0805: 104c:8034
0b:02.0 0200: 10ec:8139 (rev 10)
**0b:03.0 0280: 14e4:4320 (rev 03)**

```

lshw -C network
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a2:1f:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:30:01:d9:59:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:ea:ec:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by superprash2003 on 2008-11-25
post output of iwlist wlan0 scan from the terminal

---

### Post by IronFox on 2008-11-25
It says no networks found.

---

### Post by IronFox on 2008-11-26
FIXED!!!

Found problem in this thread --> [Seaking Hardy users with BCM4306 Wireless that fail with b43]("http://ubuntuforums.org/showthread.php?t=885173")

Just had to replace the contents of ssb_sprom file with another one on that thread and immediately it worked, and network manager picked up all the wireless in my area!

---

### Post by kevdog on 2008-11-26
Who does this fix apply too???

---

### Post by Ayuthia on 2008-11-26
> **kevdog said:**
> Who does this fix apply too???

It applies to people with the 4306 rev 03 card that cannot connect to the internet.

---

### Post by Ayuthia on 2008-11-26
> **IronFox said:**
> FIXED!!!

Found problem in this thread --> [Seaking Hardy users with BCM4306 Wireless that fail with b43]("http://ubuntuforums.org/showthread.php?t=885173")

Just had to replace the contents of ssb_sprom file with another one on that thread and immediately it worked, and network manager picked up all the wireless in my area!

Glad to see it working!  Sorry about not pointing to that earlier for you.  lwfinger mentioned that he thought it was all fixed in the 2.6.27 kernel so I thought that this was not the problem.

---

### Post by frriction on 2008-11-27
[http://backports.ubuntuforums.com/showthread.php?t=959451](http://backports.ubuntuforums.com/showthread.php?t=959451)

try this a try it works for me i have bcm4328 (rev03)
i had a same problem before it solved

---

### Post by IronFox on 2008-11-27
NOT FIXED!!!!!!

After my first reboot my bios says "401 unsupported wireless device detected.  Please remove and reboot" and now i cant boot the computer.  Im using the phoenix cME FirstBIOS f.43 for my zd8115us laptop

---

### Post by Ayuthia on 2008-11-28
> **IronFox said:**
> NOT FIXED!!!!!!

After my first reboot my bios says "401 unsupported wireless device detected.  Please remove and reboot" and now i cant boot the computer.  Im using the phoenix cME FirstBIOS f.43 for my zd8115us laptop

You will want to send this back to the other thread:
[http://ubuntuforums.org/showthread.php?t=885173](http://ubuntuforums.org/showthread.php?t=885173)
I think that it might be related.

---

### Post by Ayuthia on 2008-11-28
> **frriction said:**
> [http://backports.ubuntuforums.com/showthread.php?t=959451](http://backports.ubuntuforums.com/showthread.php?t=959451)

try this a try it works for me i have bcm4328 (rev03)
i had a same problem before it solved

That link is for the wl driver.  That driver does not support the 4306 card.

---

### Post by IronFox on 2008-11-30
My BIOS does not let me turn off my wireless during boot.  Will I have to get a replacement card?

---

