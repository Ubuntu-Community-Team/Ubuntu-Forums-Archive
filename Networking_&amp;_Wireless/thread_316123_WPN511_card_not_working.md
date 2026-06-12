---
title: "WPN511 card not working"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by andychad2 on 2006-12-10
Hi there

Just switched a couple of PC's over to Ubuntu, one is great doing exactly what I want and seems to cooperate nicely with the XP computers.  The laptop is different.  The wireless card just flashes alternate lights.  I have installed the restricted modules via synaptic and was under the impression from reading dozens of posts that it should work "out of the box" so to speak.

I am new to linux and still unsure of what the majority of you would call basic stuff.

Does anyone have any ideas?

Thanks

Andy

---

### Post by FrodoB on 2006-12-10
A little more detail please, what version of Ubuntu do you have and was it installed from the normal Live CD or from the Alternate CD, plus outputs from:

lspci

dmesg

iwconfig

---

### Post by andychad2 on 2006-12-10
Thanks for replying.

It's version 6.1 and it's from the normal live cd as far as I know. I was given the cd by a colleague.

The outputs are below, it won't le me post dmesg - too big I hope they tell you something as the look completely bewildering to me.

Cheers

andrew@andrew-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
02:03.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"netgear"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
andrew@andrew-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:23:9E:C6  
          inet6 addr: fe80::214:6cff:fe23:9ec6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-23-9E-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10162 errors:0 dropped:0 overruns:0 frame:1917
          TX packets:25178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1255796 (1.1 MiB)  TX bytes:1246311 (1.1 MiB)
          Interrupt:11 Memory:e0b60000-e0b70000 

andrew@andrew-laptop:~$

---

### Post by FrodoB on 2006-12-10
Your card seems to be recognized. Try to configure it in the Networking menu:

System -> Administration ->Networking

The tool only works for WEP or no WEP(just leave the key blank).

Give it a try and report back to us.

---

### Post by andychad2 on 2006-12-11
Frodo

I thought it should work too.  In networking it's not asking for the WEP password so I've put it in anyway and still no joy.  It's on automatic DHCP as it should be and the DNS server is correct 192.168.0.1.

The lights on the cardbus are flashing alternately.  When it's working properly they flash together.

I don't know hat I've done wrong.

Cheers

Andy

---

### Post by andychad2 on 2006-12-11
If I look in the device manager it reports an unknown device on the NIC card and the advanced links this unknown device to the wifi.

Does that give anyone any ideas?

Cheers

Andy

---

