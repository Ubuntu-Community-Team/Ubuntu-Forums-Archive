---
title: "Cannot connect to the internet"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Rittered on 2007-04-10
I have just downloaded Ubuntu, installed dual boot with windows xp, but I cannot get connected to the internet, apart from one moment when it nearly finished loading a page.

I have done "ifonfig", "iwconfig" & "lspci". Please help.


ifonfig
Link encap:Ethernet HWaddr 00:1A:4D:20:9F:72
inet addr:58.108.19.135 Bcast:58.108.19.255 Mask:255.255.255.0
inet6 addr: fe80::21a:4dff:fe20:9f72/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:590 (590.0 b) TX bytes:3389 (3.3 KiB)
Interrupt:177 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.01 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

iwconfig
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

lspci
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Momory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intela Corporation 82801GB/BR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)

There maybe some typos as I have had to type this out manually, fun o fun. Thanks in advance for the help.

---

### Post by chili555 on 2007-04-10
Well, you certainly are connected! ```
ifconfig
Link encap:Ethernet HWaddr 00:1A:4D:20:9F:72
inet addr:58.108.19.135 Bcast:58.108.19.255 Mask:255.255.255.0
``` I wonder if IPv6 may be a problem. Try this: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by DerHesse on 2007-04-10
are you behind a proxy?

---

### Post by Rittered on 2007-04-10
I'm not behind a proxy

---

### Post by DerHesse on 2007-04-10
can you ping e.g. [www.google.com]("http://www.google.com") ?

EDIT: maybe your Network interface is not supported: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63314)
What ubuntu version have you installed?

---

### Post by Rittered on 2007-04-10
no I can't ping google. I think version 6.

---

### Post by chili555 on 2007-04-10
If you have not, please follow the instructions above to blacklist IPv6. Reboot. Did that fix it? If not, please let us see the output of these commands in a terminal:```
ping -c3 www.google.com
ping -c3 64.233.161.147
```Thanks.

---

### Post by Rittered on 2007-04-10
disbaling IPv6 didn't help

ping -c3 [www.google.com](www.google.com) = unknown host
ping -c3 64.233.161.147 = network is unreachable

---

### Post by darkwill on 2007-04-10
I'm having the exact same problem. here's my ifonfig, iwconfig and lspci:

ifconfig spits out
eth0      Link encap:Ethernet  HWaddr 00:30:18:20:EB:F7  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fe20:ebf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1423972 (1.3 MiB)  TX bytes:152988 (149.4 KiB)
          Interrupt:10 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:70:30:81:92  
          inet6 addr: fe80::21a:70ff:fe30:8192/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:2736 (2.6 KiB)
          Base address:0x6000 

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-70-30-81-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x6000 


iwconfig says:
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

finally lspci says:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)


I'm running Edgy (upgraded from Dapper) and I'm not sure if IPv6 is enabled, but I get the same responses to the pings as Rittered. I'm not behind a proxy.

I'm running a Linksys 802.11g card in my computer and am trying to connect it to a Belkin 802.11g router. (I doubt this woud matter, but I guess it couldn't hurt to  post it.)

Any and all help or leads would be appreciated. It's possible that Feisty will cure some of my problems (hopefully...)

Thanks for lookin,
Will

---

### Post by chili555 on 2007-04-10
It's probably not going to connect with your wired ethernet connected and holding an IP address. Please disconnect the ethernet cable, restart networking *sudo /etc/init.d/networking restart* and tell us what happens with wlan0.

---

### Post by darkwill on 2007-04-10
ok. thanks for the interest :)

here's what came up when i restarted:> 
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wmaster0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
There is already a pid file /var/run/dhclient.eth0.pid with pid 3451
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:30:18:20:eb:f7
Sending on   LPF/eth0/00:30:18:20:eb:f7
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4919
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1a:70:30:81:92
Sending on   LPF/wlan0/00:1a:70:30:81:92
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up ath0.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Input/output error
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1a:70:30:81:92
Sending on   LPF/wlan0/00:1a:70:30:81:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


---

### Post by chili555 on 2007-04-11
Not a word about wlan0? With the wire disconnected, please do ```
iwlist wlan0 scan
``` It sometimes takes a few tries, so don't be afraid to try 3-4 times. We need the ESSID and MAC address of the access point to readily connect.

---

### Post by darkwill on 2007-04-11
without ANY hesitation it just says
> wlan0        No Scan Results

I retyped it about 10 times and it kept saying No Scan Results instantly..
I'll try reinstalling the driver with ndiswrapper and see what happens from there.

Update: after some more researching I come to find out this>  *-network:0
             description: Wireless interface
             [B]product: RT2561/RT61 802.11g PCI
             vendor: RaLink[/B]
             physical id: 9
             bus info: pci@00:09.0
             logical name: wmaster0
             version: 00
             serial: 00:1a:70:30:81:92
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list logical wireless ethernet physical
             configuration: broadcast=yes **driver=rt61pci** driverversion=CVS firmware=.bin link=yes multicast=yes
wireless=IEEE 802.11g
             resources: iomemory:e6000000-e6007fff irq:11


---

