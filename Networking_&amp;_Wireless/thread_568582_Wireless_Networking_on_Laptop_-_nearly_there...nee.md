---
title: "Wireless Networking on Laptop - nearly there...need a push"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by akonvert on 2007-10-06
Hi there,

I have a compaq presario v4000 with a Intel Pro Wireless 2200bg card.

I have just installed kubuntu, and for the last week have been trying unsuccessfully to connect to my wireless router in my home.

I have googled alot to get it working and have made some progress, but for some reason still cannot connect.

1. My etc/network/interfaces says this: (eth1 is my wireless interface, and eth0 is my ethernet interface.)

****************************
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid ournet
wireless-key passw (note: this is a temp password)

auto eth0
iface eth0 inet dhcp
***********************************

2. iwconfig says this: (ournet is the essid on my router)

************************************

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"ournet"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*********************************

3. When i type "iwlist eth1 scan" i get a list of all of the wireless networks in my building including my own.

4. I have uninstalled KNetworkManager because it never appeared to show the scan results that iwconfig did. I then installed Kwlan which always scans and successfully identifies all of the results that iwconfig does.

5. When I start the computer, Kwlan appears to have connected to the network (i.e. the icon in the tray is the 'connected' icon, and when I hover over it a popup appears saying "interface eth1 connected to ournet".

6. At this stage I thought all was going really well, so I opened Firefox and navigated to my home page, but the page request timed out.

7. I pinged the ip address of my local network, but got no results.


I feel I am almost there, but my noob-ness is letting me down. is there anyone who can give me a hand here? If so it would be much appreciated.

Many Thanks.

---

### Post by Stebalien on 2007-10-06
if you are using feisty I would use the NetworkManager applet (in the system tray/Notification area).
otherwise use the network-admin (system->Administration->Network).
if you need to use the command line read this [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by kevdog on 2007-10-06
Ok you maybe having a problem with either your route path or DNS servers.

Lets verify that you are actually connected to the router
ping 192.168.1.1 <--- or whatever the router address is
cat ifconfig eth1

Can you post 
route -n

This will give us information about the gateway (which should be your router).

To isolate a potential DNS problem, can you at a minimum ping google by ip address and not name:
ping 64.233.187.99  <--- This is google's IP

---

### Post by akonvert on 2007-10-06
Hi Kevdog and Stebalien,

Many thanks for your replies. I have carried out the tests that you asked for and here are the results:

TEST 1:

root@CALIGULA:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.182 icmp_seq=12 Destination Host Unreachable
From 192.168.0.182 icmp_seq=13 Destination Host Unreachable
From 192.168.0.182 icmp_seq=14 Destination Host Unreachable
From 192.168.0.182 icmp_seq=16 Destination Host Unreachable
From 192.168.0.182 icmp_seq=17 Destination Host Unreachable
From 192.168.0.182 icmp_seq=18 Destination Host Unreachable
From 192.168.0.182 icmp_seq=20 Destination Host Unreachable
From 192.168.0.182 icmp_seq=21 Destination Host Unreachable
From 192.168.0.182 icmp_seq=22 Destination Host Unreachable
From 192.168.0.182 icmp_seq=24 Destination Host Unreachable
From 192.168.0.182 icmp_seq=25 Destination Host Unreachable
From 192.168.0.182 icmp_seq=26 Destination Host Unreachable
From 192.168.0.182 icmp_seq=28 Destination Host Unreachable
From 192.168.0.182 icmp_seq=29 Destination Host Unreachable
From 192.168.0.182 icmp_seq=30 Destination Host Unreachable 

***NOTE: These ping results are interesting because the IP address that the ping is coming from is the IP address that is usually assigned to the ethernet connection (eth0). Hmmmm....


TEST 2:

root@CALIGULA:~# cat ifconfig eth1
cat: ifconfig: No such file or directory
cat: eth1: No such file or directory


TEST 3:

root@CALIGULA:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

What do you make of these results?

Many Thanks

---

### Post by akonvert on 2007-10-06
Oh, I forgot the 4th test.

root@CALIGULA:~# ping 64.233.187.99
connect: Network is unreachable  


Just to give you some more info, this is what happens when I attempt to connect using the dhclient command

root@CALIGULA:~# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5346
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

---

### Post by kevdog on 2007-10-06
It doesnt seem like you are getting an IP address.  Just to confirm this please post

ifconfig

And are you sure this is the entire output of the following:
root@CALIGULA:~# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5346
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on LPF/eth1/00:12:f0:c8:44:3b
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

Can you post in addition
lshw -C network

---

### Post by akonvert on 2007-10-06
Hi kevdog,

I have run the tests that you asked. Here are the results:

TEST 1:

root@CALIGULA:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:D4:76:D4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x4400

eth1      Link encap:Ethernet  HWaddr 00:12:F0:C8:44:3B
          inet6 addr: fe80::212:f0ff:fec8:443b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:357 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 Memory:b0106000-b0106fff

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E4:D4:76:D4
          inet addr:169.254.10.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x4400

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:C8:44:3B
          inet addr:169.254.6.130  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 Memory:b0106000-b0106fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3462 (3.3 KiB)  TX bytes:3462 (3.3 KiB)

**********************************************************************

TEST 2: 

root@CALIGULA:~# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5252
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

****************************************************************

TEST 3:

root@CALIGULA:~# lshw -C network
  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@06:05.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:c8:44:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:b0106000-b0106fff irq:18
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:d4:76:d4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:3000-30ff iomemory:b0109400-b01094ff irq:18




I hope this is what you are after. 

Many Thanks.

---

### Post by kevdog on 2007-10-06
You are not getting an IP address from the router -- so that is the main problem.

You cant run wired and wireless at the same time, which I dont think you are, but just to make sure.

Can you post:
iwlist scan

---

### Post by akonvert on 2007-10-06
Hi kevdog,

Yeah, I always only run one connection at a time. When I want to use wireless I have been rebooting with the ethernet cable unplugged, just to make sure.

The results of iwlist scan are:

root@CALIGULA:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:E3:FB:61:71
                    ESSID:"BWClark Sharebrokers Ltd"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 180ms ago


          Cell 02 - Address: 00:15:E9:E4:0F:C7
                    ESSID:"ournet"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-41 dBm
                    Extra: Last beacon: 404ms ago


          Cell 03 - Address: 00:15:E9:2A:4D:06
                    ESSID:"coolerthanharleigh"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm
                    Extra: Last beacon: 496ms ago


          Cell 04 - Address: 00:15:E9:E4:1C:BB
                    ESSID:"SuntechNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm
                    Extra: Last beacon: 1580ms ago


          Cell 05 - Address: 00:18:4D:AD:38:B8
                    ESSID:"The Secret Enterprise"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm
                    Extra: Last beacon: 9296ms ago


          Cell 06 - Address: 00:1B:11:15:6B:04
                    ESSID:"DLINK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm
                    Extra: Last beacon: 9404ms ago


          Cell 07 - Address: 00:17:9A:12:46:A8
                    ESSID:"DLINK_WIRELESS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm
                    Extra: Last beacon: 8320ms ago

******************************************************************


Strange huh, The wireless interface can scan and look at other networks but can't connect.

Just incase you were wondering, I have only enabled WEP security on the router, and have also removed all IP and MAC address filters. I have also set the IP address allocation on the router to DHCP.

Anyway, let me knwo what you think.

Thankyou, once again.

---

### Post by kevdog on 2007-10-07
Of all those wireless networks, which one are you trying to connect to???

Can you try to connect manually like this:

sudo ifdown eth1
sudo ifup eth1
sudo iwconfig eth1 essid "ournet"
sudo iwconfig eth1 key HEXKEYHERE <----- note if using ASCII key instead of HEX key use s:ASCII_KEY
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

---

### Post by akonvert on 2007-10-07
I am trying to connect to the network with essid "ournet".

---

### Post by kevdog on 2007-10-07
Please see reply above, I just made an edit to it!!

---

### Post by akonvert on 2007-10-07
Hi kevdog,

I tried the commands that you requested and got the following:

STEP 1: sudo ifdown eth1
root@CALIGULA:~# sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 5152
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback

******************************************************

STEP 2: sudo ifup eth1

root@CALIGULA:~# sudi ifup eth1
bash: sudi: command not found
root@CALIGULA:~# sudo ifup eth1
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "passw".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

********************************************************

STEP 3: 
root@CALIGULA:~# sudo iwconfig eth1 essid "ournet"
root@CALIGULA:~# sudo iwconfig eth1 key s:passw
root@CALIGULA:~# sudo iwconfig eth1 mode Managed
root@CALIGULA:~# sudo ifup eth1
ifup: interface eth1 already configured

*******************************************************

STEP 4: sudo dhclient eth1

root@CALIGULA:~# sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5243
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

*******************************************************

Not much different really. What do you think?

---

### Post by kevdog on 2007-10-07
Ok lets try the following (weird messages you are getting)

```

sudo ifconfig eth1 down
sudo ifconfig eth1 0.0.0.0
sudo ip route flush dev eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ournet"
sudo iwconfig eth1 key s:passw
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

```

Are you using 64 or 128 WEP???
Are you using 32 or 64 bit Ubuntu?

---

### Post by akonvert on 2007-10-07
Hi kevdog,

Here are the results of the set of commands:

root@CALIGULA:~# sudo ifconfig eth1 down
root@CALIGULA:~# sudo ifconfig eth1 0.0.0.0
root@CALIGULA:~# sudo ip route flush dev eth1
Nothing to flush.
root@CALIGULA:~# sudo ifconfig eth1 up
root@CALIGULA:~# sudo iwconfig eth1 essid "ournet"
root@CALIGULA:~# sudo iwconfig eth1 key s:passw
root@CALIGULA:~# sudo iwconfig eth1 mode Managed
root@CALIGULA:~# sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:f0:c8:44:3b
Sending on   LPF/eth1/00:12:f0:c8:44:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


***********************************************************

To answer your other questions:

1. I am using 64 bit WEP.
2. I am using 32 bit ubuntu with KDE interface.

---

### Post by kevdog on 2007-10-07
What happens if you turn WEP off?? Can you connect to an unencrypted network??  If you can with the same series of commands that you just typed --- minus the key line (since you are not using WEP), at least we can verify that your driver is good.  If unencrypted works, what about 128 WEP?? or what about using the 10 character hex key instead of the ascii password???

---

### Post by akonvert on 2007-10-09
Hi kevdog,

Apologies for the delay in getting back to you. I have been having issues getting my Kubuntu installation to boot over the last day, so decided to bite the bullet and do a full install of Ubuntu (with Gnome) Gutsy Gibbon Beta.

The result is good news....everything installed without a hitch including my wireless connection....no configuration. Strange. I wish I knew why. Either there is an issue with wireless networking in Feisty Fawn, or Kubuntu.

Anyway, thanks for all your help. It is much appreciated.

---

