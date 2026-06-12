---
title: "WG511T wireless card doesn't work"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by karohan on 2006-08-14
I recently configured a Netgear WG511T wireless card, which is supposed to be supported by Ubuntu "out of the box". However, while to some point that may be true, it really is not. I mean when I insert my wireless card into my Dell Inspiron 1100, it is apparently being detected and I can configure its settings and all, such as my WEP key and connecting to my ESSID. When I finished configuring the device, I see no errors at all and it seems to be connected. The signal strength is even in the 90%'s. But whenever I connect to the internet with it, it doesn't work. Meaning that it doesn't connect to the internet. When I went to System>Administration>Network Tools and I saw the settings for my wireless card (which was labeled atho0 and was recognized), the IP address was different that what it should have been. When I connect to internet via my ethernet cable, which works successfully, the IP address is different. I figured that may be the problem, but I don't know how to fix it. Any ideas?

I don't know if this helps or not, but before reformatting my hard drive for dual-booting Ubuntu and Windows, I had only Windows on it. I attempted to connect to the internet wirelessly in Ubuntu through the LiveCD and then it worked. But for some reason its not working right now.

---

### Post by stormblue on 2006-08-14
Hey, just becuase it has a different IP address it isn't a big deal.  You're probably using DHCP.

I'm not sure of anything new to try other than configure it through the Command Line.

---

### Post by stormblue on 2006-08-15
I have this card and it works right out of the box with WEP for me configured from the command line.

---

### Post by karohan on 2006-08-21
It used to work for me too right out of the box, but now it doesn't. I'm using a 686 kernel and I use 128-bit WEP security, if that makes any difference. I can't configure it from the command line because it says the operation isn't permitted. The other thing is that when I configure it, my card's two lights are blinking simultaneously, which should indicate that its connected to my router. Also, you said that if my wireless card and ethernet had different IP's it shouldn't make a difference. But they were different at the same time, so even if I am using DHCP, they should be the same shouldn't they?

---

### Post by lupine_nickt on 2006-08-21
If you want to use your wireless card **or** your ethernet card, and have the same IP address regardless of which you use, then you should set up one f them to spoof the MAC address of the other (this is trivial - "sudo ifconfig <interface> hw ether <other-interface-MAC-address>"). chances are, one or the other of the two will support it. 

However, that's unlikely to be the problem. Can you post the output of "ip route show", by any chance? 

I'm guessing that your computer is set up by default to send all data to your ethernet interface, hence the problems.

Should be easy enough to fix :-
```

sudo ip route del default via <gateway-ip> dev eth0
sudo ip route add default via <gateway-ip> dev ath0

```

xF,

...Nick

---

### Post by karohan on 2006-08-21
Ok, when I typed in ip route show I got this:
```
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2
192.168.0.0/24 dev ath0  proto kernel  scope link  src 192.168.0.4
default via 192.168.0.1 dev ath0
default via 192.168.0.1 dev eth0

```

It shows both the ath0 and eth0 as defaults, so I don't think it should be a problem, but I'm not sure. However, whenever I plug in my wireless card, my entire internet connection doesn't work, even if my ethernet connection is plugged in and is put as my default. However, now when I go to network tools, the card is shown as "unknown device" so I figure that may be a problem.

---

### Post by lupine_nickt on 2006-08-21
You can't run them both at the same time, in the same subnet. Disable one or the other and see how you get on.

xF,

...Nick

---

### Post by thepletts on 2008-03-19
I also have a Netgear WG511T  rev 01 PCI wireless network card which works fine in Windows, but does not seem to be working under Ubuntu 7.10, either the live CD or HD install.  

The lights blink.  I'm prompted for the WEP password when trying to connect to a WEP encrypted network.  However, it gives not connection and seemingly assigns no IP number after entering the password, or when trying to connect to an open, unencrypted connection.

In System|Administration|Restricted Drivers, the Atheros HAL layer drivers are installed and enabled.  
Sometimes the wireless “bars” show up in the NM icon, so seemingly I'm connected.  However, I can't access the internet and when right-clicking Network Manager, the connection information shows no IP number.

Here are the results of some commands recommended in other parts of the forum.

Any help or ideas to get it working would be appreciated.

**/etc/network/interfaces** contains the following:
auto lo
iface lo inet loopback 

**lspci **
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) 
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) 
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller 
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) 

**lspci | grep -i net **
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) 

**sudo lshw -C network **
  *-network               
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       logical name: eth0 
       version: 01 
       serial: 00:0d:56:a8:52:ce 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s 
  *-network 
       description: AR5001-0000-0000 
       product: Wireless LAN Reference Card 
       vendor: Atheros Communications, Inc. 
       physical id: 0 
       version: 00 
       slot: Socket 0 
       resources: irq:11 
  *-network 
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications, Inc. 
       physical id: 1 
       bus info: pci@0000:03:00.0 
       logical name: wifi0 
       version: 01 
       serial: 00:09:5b:c7:20:bb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 

**sudo iwlist scan **
lo        Interface doesn't support scanning. 
eth0      Interface doesn't support scanning. 
wifi0     Interface doesn't support scanning. 
ath0      Scan completed : 
          Cell 01 - Address: 00:11:09:99:FB:EF 
                    ESSID:"XXXXX" 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=26/70  Signal level=-69 dBm  Noise level=-95 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 54 Mb/s; 9 Mb/s; 18 Mb/s 
                              36 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
          Cell 02 - Address: 00:0F:CB:AD:A0:E8 
                    ESSID:"XXXXX" 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
[B]
sudo iwconfig [/B]
lo        no wireless extensions. 
eth0      no wireless extensions. 
wifi0     no wireless extensions. 
ath0      IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off 
          Link Quality=0/70  Signal level=-88 dBm  Noise level=-88 dBm 
          Rx invalid nwid:6735  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

**route **
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
link-local      *               255.255.0.0     U     0      0        0 eth0 
default         *               0.0.0.0         U     1000   0        0 eth0 

**sudo dhclient **
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wifi0: unknown hardware address type 801 
wifi0: unknown hardware address type 801 
Listening on LPF/ath0/00:09:5b:c7:20:bb 
Sending on   LPF/ath0/00:09:5b:c7:20:bb 
Listening on LPF/wifi0/ 
Sending on   LPF/wifi0/ 
Listening on LPF/eth0/00:0d:56:a8:52:ce 
Sending on   LPF/eth0/00:0d:56:a8:52:ce 
Sending on   Socket/fallback 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

**sudo ifconfig **
ath0      Link encap:Ethernet  HWaddr 00:09:5B:C7:20:BB  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

ath0:avah Link encap:Ethernet  HWaddr 00:09:5B:C7:20:BB  
          inet addr:169.254.7.60  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

eth0      Link encap:Ethernet  HWaddr 00:0D:56:A8:52:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:7 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:56:A8:52:CE  
          inet addr:169.254.8.0  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:11852 (11.5 KB)  TX bytes:11852 (11.5 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-C7-20-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:13300 errors:0 dropped:0 overruns:0 frame:1601 
          TX packets:643 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:1022263 (998.3 KB)  TX bytes:29555 (28.8 KB) 
          Interrupt:11

---

