---
title: "Dlink DWL G510 version B"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by Firewolf on 2006-10-07
(newb warning)
I think I'm very close to getting this card to work.

I've run ndiswrapper and have everything installed. The light is blinking. It can ping itself. It actually detects two wireless networks in the GUI setup.

The access point mac address it has is one letter off... is that the problem?

Any help would be appriciated.

Router information 
MAC Address:  	 00:13:10:72:93:0D  	   	 
IP Address: 	 192.168.1.1 	  	 
Subnet Mask: 	 255.255.255.0 	  	 
DHCP Server: 	 Enabled 	  	 
Start IP Address: 	 192.168.1.100  	  	 
End IP Address: 	 192.168.1.149  

content of /etc/network/interfaces
auto ath0
iface ath0 inet dhcp
wireless-essid (my essid)
wireless-key (my key)

(it seems to be getting a few packets through, but that's just recently. All week it's been getting errors, that's why there are so many)
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:D4:E1:9A
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed4:e19a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:590 errors:412618 dropped:0 overruns:0 frame:412618
          TX packets:602 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:460417 (449.6 KiB)  TX bytes:123607 (120.7 KiB)
          Interrupt:66 Memory:f8a40000-f8a50000

iwconfig
ath0      IEEE 802.11g  ESSID:"Pickett House"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:72:93:0F
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
          Rx invalid nwid:42  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

](*,)

---

