---
title: "need help using Airport with Ubuntu"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by 3dOptics on 2008-05-18
I am running Ubuntu 8.04. I do not have high speed internet, dailup internet is my only option. I want to use an airport graphite to access my dailup internet wirelessly.

First I installed the airport-utils package. I connected to the airport by clicking on the network icon in the system tray. I went to the terminal and typed airport-config, the program ran and I click on "Discover Devices", and it said: "Exception during discovery: java.io.IOException: Network is unreachable Discovery finished.". 

I solved the problem above by clicking on the network icon in the system tray and then clicking "Manual Configuration". I clicked on "Wireless Connection", then properties, and unchecked "enable roaming mode". I put in my airport network name and for the configuration I selected "Local Zeroconf network (IPv4 LL)". Then I ran the airport-config from the terminal and clicked "Discover Devices" and it shows this:

Access point found:
  Local LAN IP address:     72.251.3.163
  External IP address:      72.251.3.163
  MAC address:              0030653677ba
  Device name:              airport_graphite
  Device type:              Base Station V3.84 SN-PW0385VKH
  Uptime (days:hrs:mins):   0:00:03

In the device address box it has "10.0.1.1". I entered my password in the password box and clicked "Retrieve Settings". It shows my settings, so at this point I assume everything is working with the airport.

I went to the terminal and typed airport-modem. The program runs and in the address box is 10.0.1.1 and in the Connection status box it says "Unconnected". I click "Connect" to dail the connection, after a minute or so the Connection status changes to "Connected". I pick up the phone and I can hear the modem is connected.

I open firefox and type [www.google.com](www.google.com) and I get an Address Not Found  Firefox can't find the server at [www.google.com](www.google.com). I assume there is something else not configured right. I dont know what else I need to configure. I am assuming the problem is that I do not have something configured right with linux since I have an established connection but Ubuntu does not notice it.
Thanks in advance for any help.


Edit: Here is the output from some commands I ran after I dailed up to my isp, if it helps.

----------
iwconfig
----------
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"airport_network"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:02:2D:02:21:A4   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---------
ifconfig
---------
eth0      Link encap:Ethernet  HWaddr 00:1b:38:22:9a:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141288 (137.9 KB)  TX bytes:141288 (137.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:10:b5:df  
          inet6 addr: fe80::213:e8ff:fe10:b5df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76989 (75.1 KB)  TX bytes:148558 (145.0 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:13:e8:10:b5:df  
          inet addr:169.254.9.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-10-B5-DF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-----------------
sudo iwlist scan
-----------------
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:02:2D:02:21:A4
                    ESSID:"airport_network"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-20 dBm  Noise level=-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000003a0bddb2

----------------------------
cat /etc/network/interfaces
----------------------------
auto lo
iface lo inet loopback

iface eth0 inet ipv4ll
address 10.0.1.1
netmask 255.0.0.0

iface wlan0 inet ipv4ll
wireless-essid airport_network

auto wlan0

--------------------
dmesg | grep -i eth
--------------------
[   25.365483] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:22:9a:b8
[   25.365489] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   25.365492] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   26.041881] Driver 'sd' needs updating - please use bus_type methods
[   26.044380] Driver 'sr' needs updating - please use bus_type methods
[   45.207128] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

