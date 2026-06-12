---
title: "Gutsy wireless connection does not work/ but wired works ???"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by aio85 on 2008-01-13
Gutsy wireless connection does not work/ wired works
Hello, I'm new to Linux. I just installed the Ubuntu Gutsy distro.

I'm having Trouble accessing my wireless internet connection even though my wired connection works fine. At the top right corner, I can view my SSID but cannot connect wirelessly. Linux tries connecting wirelessly, then ultimately settles on the wired connection (which seems to work).

I've tried physically disconnecting my wired connection because I've heard there might be issues having a wired and wireless connection. Also I've tried to manually connect to the wireless connection by accessing System > Administration > Network

In the 'Connections' tab, I've selected 'Wireless Connection' and clicked 'Properties.' Under WIRELESS SETTINGS> I've set my ESSID to NETGEAR; set password type to WPA personal; left the password field empty because I do not have a WPA security-enabled network. Under CONNECTION SETTINGS> Automatic Configuration DHCP

Some relevant info:

PC: Dell Dimension 4600
wireless card: DWL G510 >> [[COLOR="Red"]Information posted in madwifi on the DWL G510[/COLOR]]("http://madwifi.org/wiki/Compatibility/D-Link")
02:01.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

----------- ROUTER CONFIGURATION SETTINGS ------------

Netgear Wireless Router
ESSID: NETGEAR
REGION: CANADA
CHANNEL: 11

Wireless Access Point
[x] Enable Access Point
[x] Allow Broadcast of Name (SSID)

Wireless Card Access List
MAC Address of wireless card has been inputted

Security Encryption WEP
Authentication Type: Automatic
Encryption Strength: Disable

-------------------------------------------

```
aio85@milkyway:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:E8:F1:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:4257 (4.1 KB)

ath0:avah Link encap:Ethernet  HWaddr 00:13:46:E8:F1:36  
          inet addr:169.254.8.42  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:07:E9:4D:93:64  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe4d:9364/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:19924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7101397 (6.7 MB)  TX bytes:1618571 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10597 (10.3 KB)  TX bytes:10597 (10.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-E8-F1-36-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68535 errors:0 dropped:0 overruns:0 frame:8102
          TX packets:2028 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5152072 (4.9 MB)  TX bytes:97465 (95.1 KB)
          Interrupt:22
```

```
aio85@milkyway:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-85 dBm  Noise level=-85 dBm
          Rx invalid nwid:65801  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by florus on 2008-01-13
Several new users including myself have had problems with wireless connectivity. The problem is inconsistent - try rebooting or putting the computer to sleep, and waking it again. This works for some of us, but we have never got to the root of the problem. My laptop is dual-boot with Vista, and the WiFi always works under Vista. The same problem existed under Feisty.

---

