---
title: "Loosing Connection to WiFi-Router unfrequently"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by an.erni on 2008-10-09
Hi guys

First of all, I'm a newbie here, so I might not provide you with the appropriate information, yet. Just tell me what you need, please. Apart from that, I'm not a native English speaker, so please forgive any typos.

I'm having problems with my WIFI-connection:
Often, everything works "out of the box". However, sometimes I lose connection. This is indicated in "Network Monitor" (which I added to the panel). As long as there is connection, the bar is green and the two monitors are black. As soon as I lost connection, there is an additional red exclemation mark next to the monitors and most of the times, the bar is yellow, but sometimes it's still green.
Sometimes it helps to go to "Manual Network Configuration" (aka "Network Settings") where I unmark and mark again the "Wireless Connection".
Another strange thing is, that the "Connection Properties: eth1" say that there's activity and the signal strength is displayed correctly. But as soon as I click "Configure", it says "The interface does not exist"...?
Apart from that, I think the issue is not connected to the Access Point, since there are other computers in the same network, where I don't encounter similar problems.

My system is as follows:
- Dell Inspiron 1501
- Ubuntu 8.04 LTS, 64bit
- WEP128-protected network

lspci -v | less
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Dell Wireless 1390 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


So I tried to follow this paper:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

1. Check for device recognition
Unfortunately, I can't find the menu "System &#8594; Preferences &#8594; Hardware Information", but if I go to "System -> Administration -> Hardware Drivers", it says that "Broadcom B43 wireless driver" is in use.

2. Check for driver
When typing "sudo lshw -C network", the only difference is that there is no IP in the last line when I lost connection:
*-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:19:7e:11:82:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=IEEE 802.11g

3. Check device is on
Same as above

4. Check for a connection to the router
Ouput of iwconfig ...
A) Connection works (no exclemation mark, green bar):
eth1      IEEE 802.11g  ESSID:"WG_Fadegrad"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:A7:B5:E0   
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-45 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
B) No connection (with exclemation mark, green bar):
eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:A7:B5:E0   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=93/100  Signal level=-41 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
C) No connection (with exclemation mark, yellow bar):
eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1C:F0:C1:A0:C9   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

As listed below, I'm NOT using WPA-encryption. So I didn't try to follow these instructions, yet.

5. Check IP assignment
Well, ifconfig doesn't display my IP even if the connection works fine. Anyhow, "sudo dhclient eth1" says...

A) Connection works (no exclemation mark, green bar):
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 36807 seconds.

B) No connection (with exclemation mark, green bar):
??? (Not tried)

C) No connection (with exclemation mark, yellow bar):
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


6. Check DNS
??? (Not tried)

7. IPv6 Not Supported
??? (Not tried)


Then, I have one last question: What's the easiest way to find a (not encrypted) WIFI-network?

Thanks in advance,
Andy

---

