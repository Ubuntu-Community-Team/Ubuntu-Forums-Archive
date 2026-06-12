---
title: "RT61 Problem *Tried Guides!*"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by pharalia on 2008-04-11
I shall start from the beginning:

I bought a D-Link DWL-G510 PCI WLAN card. I am running Gutsy 64-bit. I performed a fresh install when I upgraded to 64-bit, but the network-manager wouldn't connect (but recognised my card and displayed available networks). So I decided to tried the ndiswrapper method, but got to the extraction of the .inf file and couldn't! 

Next I have then tried downloading the driver source from Ralink, compiled and installed. The wireless card returns expected networks when issuing: 

$ sudo iwlist ra0 scan

as expected, but I am unable to connect to my router (which uses WEP). The strength of the signal is > 70% as I have bought a omni-directional antenna in an attempt to boost the signal strength!

$ sudo dhclient ra0

gives the "No DHCPOFFERS received." error and have tried the fixes for that to no avail :(

Any Suggestions?

---

### Post by dstew on 2008-04-11
Post the output of ```
cat /etc/network/interfaces
iwconfig
```It is probably a configuration problem. The driver seems to be OK.

---

### Post by pharalia on 2008-04-11
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1
iface ra0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1
auto eth0

NOTE: Tried ra0 with both static and dynamic ip's, and eth0 is set as default atm so I can bridge through a XP laptop with integrated wireless card :S

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.417 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

NOTE2: I have tried specifying the ESSID in the driver .dat file, in the interfaces file and at run-time with:

iwpriv ra0 set SSID=[name]

but still nothing :( same with the WEP key too. the rt61sta.dat file:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=[name]
NetworkType=Infra
Channel=2
AuthMode=AUTO
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=[hex key]
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0
NativeWpa=1

---

### Post by pharalia on 2008-04-11
Forgot to post the scan output too:

```
...
Cell 02 - Address: 00:11:50:EF:A7:CC
                    Mode:Managed
                    ESSID:[name]
                    Channel:2
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:73/100  Signal level:-66 dBm  Noise level:-111 dBm
...
```

---

### Post by dstew on 2008-04-11
What happens of you do **ifup ra0**? What error messages do you get? Try setting the essid and encryption key with iwconfig:```
sudo iwconfig ra0 essid [name]
sudo iwconfig ra0 key [key]
```After that, post the contents of /etc/network/interfaces again, to see if it took.

---

### Post by pharalia on 2008-04-15
I don't get any errors. Firestarter just sends status messages. The internet stops working, though. applying the attributes has no effect when set using iwconfig, the ESSID is still blank.

```
ra0       Link encap:Ethernet  HWaddr 00:1C:F0:1A:82:AE  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fe1a:82ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 
```

Strangely, the card is showing up as ethernet. I can still scan successfully though, using iwlist ra0 scan.

---

### Post by dstew on 2008-04-15
The card shows up as ethernet because that is what it is, a wireless ethernet card. It has an IP address, because you set it up for a static IP address. If your wired connection works, the wireless should also work with that setup. You can only have one interface at a time, though, so make sure your cable connection is unplugged before you try to get your wireless to work.

In addition to the ifconfig output you show above, please post the iwconfig output.

---

### Post by pharalia on 2008-04-16
Okay, I tried taking my cable connection down then bringing up my wireless but no difference. 

iwconfig:
```
ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-108 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is the output after trying to apply the ssid and wep key via iwconfig.

---

### Post by dstew on 2008-04-16
Try changing the mode to managed.

---

### Post by pharalia on 2008-04-16
Tried changing in both the driver's config file and using iwconfig.. the mode stayed as "Auto".

---

### Post by dstew on 2008-04-16
Is this the command you tried?```
sudo iwconfig ra0 mode Managed
```Did you get an error message?

---

### Post by pharalia on 2008-04-16
yeah, thats the one :) no error and no change :S luckily i am able to connect via another computer. its strange, I have never had any trouble with my laptop's wlan connection, but that is a linksys PCMCIA card. I may just go and buy the PCI version for my desktop.. at least that should work!

---

