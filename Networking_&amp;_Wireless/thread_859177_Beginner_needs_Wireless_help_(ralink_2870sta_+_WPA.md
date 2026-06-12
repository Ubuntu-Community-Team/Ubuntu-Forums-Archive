---
title: "Beginner needs Wireless help (ralink 2870sta + WPA 802.11n network) Ubuntu 8.04"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by bioshake on 2008-07-14
Hi guys,

I've found bits and pieces of info all over the place but nothing seems to be concrete and comprehensive.  What I'm looking for is a step by step guide on what us folks can do when our wireless drivers are not detected natively.

So far I have been able to compile and load a driver for my D-link DWA-140, but I simply cannot get it to connect to the network.

The confusion comes from reading about having to mess with /etc/network/interfaces and / or RT2870sta.dat and / or using the network-manager and / or using wpa_supplicant or additional configuration.

Why are there so many places to do the same thing?

Once you have your driver installed what are the next steps to get your WPA network up and running on Hardy Heron?

I see that many people give up and just go the ndiswrapper route, but my driver seems to be working I just don't understand exactly where I should be putting the configuration data to make it stick and work.

Thanks for all your time and help.

---

### Post by nickdbliss on 2008-07-14
> **bioshake said:**
> Hi guys,

I've found bits and pieces of info all over the place but nothing seems to be concrete and comprehensive.  What I'm looking for is a step by step guide on what us folks can do when our wireless drivers are not detected natively.

So far I have been able to compile and load a driver for my D-link DWA-140, but I simply cannot get it to connect to the network.

The confusion comes from reading about having to mess with /etc/network/interfaces and / or RT2870sta.dat and / or using the network-manager and / or using wpa_supplicant or additional configuration.

Why are there so many places to do the same thing?

Once you have your driver installed what are the next steps to get your WPA network up and running on Hardy Heron?

I see that many people give up and just go the ndiswrapper route, but my driver seems to be working I just don't understand exactly where I should be putting the configuration data to make it stick and work.

Thanks for all your time and help.

Go to terminal n give the output of following commands.
lspci
lshw -C network
ifconfig
iwlist scan

Thanks

---

### Post by bioshake on 2008-07-14
> **nickdbliss said:**
> Go to terminal n give the output of following commands.
lspci
lshw -C network
ifconfig
iwlist scan

Thanks

It works!

Very special thanks to aarnink for his personal help!

Basically what my problem was that I was confused between using wpa_supplicant, the driver .dat file and network-manager.

What finally got it working was using network-manager and enabling roam mode for my wireless driver INSTEAD of putting the settings in via properties (went to 'add new wireless connection').

One question now.   How do I make is so that the driver is loaded (and connects) every time Ubuntu boots up?

Thank you all very much!

---

### Post by nickdbliss on 2008-07-14
> **bioshake said:**
> It works!

Very special thanks to aarnink for his personal help!

Basically what my problem was that I was confused between using wpa_supplicant, the driver .dat file and network-manager.

What finally got it working was using network-manager and enabling roam mode for my wireless driver INSTEAD of putting the settings in via properties (went to 'add new wireless connection').

One question now.   How do I make is so that the driver is loaded (and connects) every time Ubuntu boots up?

Thank you all very much!

Which driver u are using ?

---

### Post by bioshake on 2008-07-14
> **nickdbliss said:**
> Which driver u are using ?

The latest that ralink has:

[http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=72081&d=1212092760](http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=72081&d=1212092760)

Damnit!  I rebooted and now I can't get the network-manager to come up with the list of Wireless options that it had before I rebooted and I'm having a problem figuring out how I got it there :(

I thought I just went into 'manual configuration' and set it to roaming and it showed up but that's not working so i'll have to figure something else out ..

:(

Wireless on Ubuntu is hard!

If I specify a manual configuration using network-manager and then go back to roaming mode I can get the list to come up again but I'm still having problems getting the connection I had just prior to the reboot :(

Going to keep trying.. the list of networks comes up including mine but it sticks at 30% and then fizzles out.

---

### Post by bioshake on 2008-07-16
> **nickdbliss said:**
> Go to terminal n give the output of following commands.
lspci
lshw -C network
ifconfig
iwlist scan

Thanks

Here is the info you requested (I can't get it to work again :().  All I did was reboot (because there were some updates it found (SSL open SSL) and I installed the Ati graphics driver.  When I rebooted I went into hardware manager and clicked the checkbox next to the "RT2870 Wireless lan driver" to enable it.

lspci

mediabox@mediabox-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0c.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)


lshw -C network

mediabox@mediabox-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 11
       serial: 00:13:49:17:4f:66
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-velocity driverversion=1.14 latency=32 maxlatency=8 mingnt=3 module=via_velocity multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1c:f0:da:cb:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless


ifconfig

mediabox@mediabox-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:49:17:4f:66  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15575 (15.2 KB)
          Interrupt:16 Base address:0xe800 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:49:17:4f:66  
          inet addr:169.254.4.37  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65952 (64.4 KB)  TX bytes:65952 (64.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:1c:f0:da:cb:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1896 errors:0 dropped:0 overruns:3137 frame:3137
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:212936 (207.9 KB)  TX bytes:22240 (21.7 KB)


mediabox@mediabox-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:12:17:CA:74:D5
                    ESSID:"RockWAP"
                    Mode:Managed
                    Channel:1
                    Quality:56/100  Signal level:-84 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1C:F0:55:BE:EB
                    ESSID:""
                    Mode:Managed
                    Channel:4
                    Quality:82/100  Signal level:-58 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:18:F8:E8:DC:1E
                    ESSID:"Bryant"
                    Mode:Managed
                    Channel:6
                    Quality:80/100  Signal level:-60 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:13:D4:0B:8F:61
                    ESSID:"BLACK"
                    Mode:Managed
                    Channel:11
                    Quality:82/100  Signal level:-58 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s


iwconfig ra0

mediabox@mediabox-desktop:~$ iwconfig ra0
"  Nickname:"RT2870STA"ss  ESSID:"TyBox
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:169
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


RT2870STA.dat

mediabox@mediabox-desktop:~/Altered/os/linux$ sudo cat /etc/Wireless/RT2870STA/RT2870STA.dat 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=US
ChannelGeography=1
SSID=TyBox
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<passkeyinhex>
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0

mediabox@mediabox-desktop:~/Altered/os/linux$ sudo dhclient ra0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:1c:f0:da:cb:14
Sending on   LPF/ra0/00:1c:f0:da:cb:14
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.140 on ra0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.140 on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.140
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

One interesting point is on the "iwconfig ra0" There are quotes which are scattered and extra characters in there - might this be confusing it?   where are they coming from?  IE:  the ss after "RT2870STA"ss.   Thanks again for the help!

---

### Post by bioshake on 2008-07-16
Also here is a screenshot that shows me connected (even though I'm not) - I had it working once it must be some minor detail that was changed when I clicked on the box next to the driver in hardware manager?

I've also  noticed when I keep doing iwconfig (right after I click on a network) that the data for "Cell:" keeps changing.  Is that the hardware mac address for the Access Point (router?).

---

### Post by bioshake on 2008-07-16
Looks like I've got it working again.  Hopefully it will last through the next reboot.

I used WPA2 instead of WPA (ALL my other wireless devices use WPA and work fine) but my router is set to support both which apparently why it worked.

I'm not going to complain unless it stops working again :)

---

### Post by aarnink on 2008-07-16
Bioshake,

after inserting the module it is loaded, but it wont load automatically during the next boot. To load the module rt2870sta.ko automatically you can install it by adding install during make.

$make && install

---

