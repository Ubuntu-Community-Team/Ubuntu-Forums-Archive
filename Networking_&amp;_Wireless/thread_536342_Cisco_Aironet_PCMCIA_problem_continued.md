---
title: "Cisco Aironet PCMCIA problem continued"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by Barkingdoggy on 2007-08-27
Dual-boot laptop running Feisty.  Cisco Aironet 340 works fine booted into Windows.  Booted into Ubuntu, it detects the card and the network, but Ubuntu does not connect to the network.  I've tried different access points (Linksys, Netgear, Adaptek) and different networks.  Each/all of these networks are open, public networks.  TIA for your assistance.  - Barkingdoggy

FYI:

cat /proc/driver/aironet/eth1/Status
```
Status: CFG ACT SYN LNK 
Mode: 3f
Signal Strength: 95
Signal Quality: 5
SSID: Wireless
AP: 
Freq: 0
BitRate: 11mbs
Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
Device: 340 Series
Manufacturer: Cisco Systems
Firmware Version: 4.25.30
Radio type: 2
Country: 0
Hardware Version: 11
Software Version: 425
Software Subversion: 1e
Boot block version: 143
```

cat /proc/driver/aironet/eth1/Config
```
Mode: ESS
Radio: on
NodeName:                 
PowerMode: CAM
DataRates: 2 4 11 22 0 0 0 0
Channel: 6
XmitPower: 30
LongRetryLimit: 16
ShortRetryLimit: 16
RTSThreshold: 2312
TXMSDULifetime: 5000
RXMSDULifetime: 10000
TXDiversity: both
RXDiversity: both
FragThreshold: 2312
WEP: open
Modulation: cck
Preamble: short
```

iwconfig
```
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-51 dBm  Noise level=-91 dBm
          Rx invalid nwid:58  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:17276   Missed beacon:315
wifi0     IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-51 dBm  Noise level=-91 dBm
          Rx invalid nwid:58  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:17276   Missed beacon:315
```


less /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Wireless

auto wlan0

/etc/network/interfaces (END) 
```

---

### Post by Barkingdoggy on 2007-08-27
MORE INFO...

lshw -C network
```

  *-network               
       description: Cisco Systems
       physical id: 0
       version: 340 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a5:d5:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.50 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:8c00-8cff iomemory:d0003000-d0003fff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:40:96:33:16:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
```

---

### Post by Barkingdoggy on 2007-08-27
MORE INFO...

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:30:AB:22:AE:E8
                    ESSID:"Wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-43 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

wifi0     Scan completed :
          Cell 01 - Address: 00:30:AB:22:AE:E8
                    ESSID:"Wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-43 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
```

---

### Post by Barkingdoggy on 2007-08-27
MORE INFO...

Connections listed under Network Manager are Wireless Connection (wifi0), Wireless Connection (eth1), Wired Connection (eth0) and Modem Connection.  The two wireless connections are set to Enable roaming mode.  If I try to manually configure them, Network Manager forces me to use WEP, so I do so and leave the Network password box empty.  But that doesn't work...

---

### Post by Barkingdoggy on 2007-08-27
sudo dhclient wifi0    (similar output for commands dhclient eth1 and wlan0)
```
There is already a pid file /var/run/dhclient.pid with pid 11538
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by wirelessmonkey on 2007-08-28
> **Barkingdoggy said:**
> Dual-boot laptop running Feisty.  Cisco Aironet 340 works fine booted into Windows.  Booted into Ubuntu, it detects the card and the network, but Ubuntu does not connect to the network.  I've tried different access points (Linksys, Netgear, Adaptek) and different networks.  Each/all of these networks are open, public networks.  TIA for your assistance.  - Barkingdoggy

FYI:

cat /proc/driver/aironet/eth1/Status
```
Status: CFG ACT SYN LNK 
Mode: 3f
Signal Strength: 95
Signal Quality: 5
SSID: Wireless
AP: 
Freq: 0
BitRate: 11mbs
Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
Device: 340 Series
Manufacturer: Cisco Systems
Firmware Version: 4.25.30
Radio type: 2
Country: 0
Hardware Version: 11
Software Version: 425
Software Subversion: 1e
Boot block version: 143
```

cat /proc/driver/aironet/eth1/Config
```
Mode: ESS
Radio: on
NodeName:                 
PowerMode: CAM
DataRates: 2 4 11 22 0 0 0 0
Channel: 6
XmitPower: 30
LongRetryLimit: 16
ShortRetryLimit: 16
RTSThreshold: 2312
TXMSDULifetime: 5000
RXMSDULifetime: 10000
TXDiversity: both
RXDiversity: both
FragThreshold: 2312
WEP: open
Modulation: cck
Preamble: short
```

iwconfig
```
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-51 dBm  Noise level=-91 dBm
          Rx invalid nwid:58  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:17276   Missed beacon:315
wifi0     IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-51 dBm  Noise level=-91 dBm
          Rx invalid nwid:58  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:17276   Missed beacon:315
```


less /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Wireless

auto wlan0
{{ you didn't include wifi0 here}}

/etc/network/interfaces (END) 
```



Lets try things manually first, and see what we can get working.   Right click and quit network manager.


In terminal.
# sudo ifconfig eth1 down
# sudo ifconfig wifi0 down
# sudo ifconfig eth1 up 
sudo iwconfig eth1 essid "Wireless(or name of other open network)
sudo dhclient eth1

Do you get an address at this point?

Try for your other wireless adapter.

Keep logs of all the data you get back, and we'll debug your connections.

---

### Post by Barkingdoggy on 2007-08-30
I reinstalled Ubuntu/Fiesty and formatted the partitions to get a clean install.  Now I have kernel 2.60.16, instead of .15 earlier.  The same problems remain, however.  Still no connection to an open network access point.  Here's the output from manually trying to connect on eth1 and wifi0 (virtually the same output for both);

dhclient eth0
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:33:16:aa
Sending on   LPF/eth1/00:40:96:33:16:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
The linux kernel supports the Aironet pcmcia cards/drivers.  They are supposed to work well "out of the box."  What am i doing wrong?  TIA - Barkingdoggy

---

### Post by fenway on 2007-08-31
I had similar problem and even tried installing it with Kubuntu and reinstalling it back to ubuntu again but still failed till by luck I managed to obtain the IP address by first executing the 

sudo dhclient wifi0, follow by 
sudo dhclient eth2

I think for you would be wifi0 first then eth1. Cant seem to make sense how this will works but you may want to give it a try.. good luck

---

### Post by fenway on 2007-09-01
I tried by just executing sudo dhclient eth2 and it worked, would like to know how to configure the wlan to automatically discover and grab an IP from the wireless router ?

---

### Post by Barkingdoggy on 2007-09-04
Fenway - Your suggestion did not work for me.  Someone told me my problem is a configuration/driver problem, because "lshw -C network" does not show a driver associated with the Cisco card.  But, in Device Manager, I see a "340 Series Wireless LAN Adapter" and info.linux.driver is listed as airo_cs.  

Someone else has suggested installing Cisco's Aironet Client Utilities.  When I try to do this, I get a message saying I have to have root permissions to do so, in spite of having done "sudo -s" and "sudo sh install"  to execute the install script downloaded.

Suggestions?  - Barkingdoggy

---

### Post by Barkingdoggy on 2007-09-05
I give up.  I obtained a Netgear WG511T card, popped it in and turned my computer on.  Ubuntu recognized it, loaded a proprietary Atheros driver and it works!  Bye-bye Cisco.

Barkingdoggy.

---

