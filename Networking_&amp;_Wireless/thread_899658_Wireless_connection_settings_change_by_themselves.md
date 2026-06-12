---
title: "Wireless connection settings change by themselves"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Mariane on 2008-08-24
Hi all, 

I now this title sounds strange, but this is exactly what happens. I surf for a while and suddently I get "Server not found" errors. When I check my connection setting they are not as I left them. For example, the search domain field, which I leave blank, displays "vodaphone". 

I change them back and it works fine. For a while. I started using this connection 3 days ago and it has happened 3 times. 

I add below the resuls of the recommended tests (which I don't understand but I'm sure someone will understand). 

Please help. 

Mariane


lshw -C network:
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:ba:39:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet 
	physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.42 latency=0 
	module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:90:f5:68:7c:f4
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical 
	tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 
	driverversio             n=2.2LK duplex=half latency=0 link=no module=r8169 
	multicast=yes port=twisted pair



iwconfig:
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"ZyXEL_X90"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:CF:53:68:DB
          Bit Rate=48 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=82/100  Signal level=-62 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:90:f5:68:7c:f4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:216 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20084 (19.6 KB)  TX bytes:20084 (19.6 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1d:e0:ba:39:13
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:feba:3913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14072181 (13.4 MB)  TX bytes:2788189 (2.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-BA-39-13-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Mariane on 2008-08-28
Hello? Could someone please answer, even if it is just to tell me "I have the same problem and I have never been able to solve it"? 

I'm starting to feel lonely out there... 

Mariane

---

### Post by urk_nono on 2008-08-28
I've seen a few other people having trouble with their 4965AGN networks. I do too and currently researching how to fix it.

---

### Post by Mariane on 2008-09-10
Thank you Urk Nono. 

It seems to be only with this wireless connection, when I'm 
connected elsewhere via a wire it does not happen. 

Mariane

---

