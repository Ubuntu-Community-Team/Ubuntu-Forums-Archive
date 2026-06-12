---
title: "Wifi not working, Broadcom BCM4313"
date: 2014-08-05
forum: Networking &amp; Wireless
---

### Post by TheElder777 on 2014-08-05
Hey all. I just moved to my new apartment and surprisingly I can not connect to my new wifi (I was able to do so before moving). It will stay "connecting" but will never connect. I have Ubuntu 12.04 and I have no internet access on the machine in question. I have a laptop that I am able to access my wifi with and I am able to transfer files to the bad machine via usb. I have read countless threads and googled many times before resorting to a new post. I am in need of some help and I hope someone can shed some light. Here are some commands.

```

[*]lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

[*]sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c0:18:85:2a:01:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:fe500000-fe503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: d4:be:d9:9b:6c:ae
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:fe400000-fe40ffff

[*]ifconfig 
eth0      Link encap:Ethernet  HWaddr d4:be:d9:9b:6c:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr c0:18:85:2a:01:43  
          inet6 addr: fe80::c218:85ff:fe2a:143/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:4 dropped:0 overruns:0 frame:12429
          TX packets:164 errors:79 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1968 (1.9 KB)  TX bytes:36525 (36.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39320 (39.3 KB)  TX bytes:39320 (39.3 KB)

[*]rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```
ANY help will be appreciated. Thank you for reading and your time.

PS: I would like to remind you that my Ubuntu machine has NO internet access at all.

---

### Post by Hadaka on 2014-08-06
Hi, give this a try and you dont have to haul any files
they are already there,
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -v brcmsmac
sudo rfkill unblock all
```
boot
see if that works for you

---

### Post by TheElder777 on 2014-08-06
> **Hadaka said:**
> Hi, give this a try and you dont have to haul any files
they are already there,
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -v brcmsmac
sudo rfkill unblock all
```
boot
see if that works for you

WOOOOW. That worked perfectly. THANK YOU SO MUCH!!!

Just to make sure I get what I did, we removed the driver (along with config files) and then placed them back?

---

### Post by Hadaka on 2014-08-06
Hi glad that worked !

what you did was remove the WL driver bcmwl-kernel-source
and activated the native dirver already in the kernel 
 brcmsmac

and issued an unblock all rfkill command.

*removed wrong driver...inserted correct driver

---

### Post by TheElder777 on 2014-08-06
> **hadaka said:**
> hi glad that worked !

What you did was remove the wl driver bcmwl-kernel-source
and activated the native dirver already in the kernel 
 brcmsmac

and issued an unblock all rfkill command.

*removed wrong driver...inserted correct driver

thank you!

---

### Post by TheElder777 on 2015-03-11
Hello again... I apologize for resurrecting this thread back, but it is a very similar problem, I tried using the same commands but it didn't work this time : ( If you can help me that would be great. Once again, here are some commands: 


```

------------------------------------
lsb_release -a
------------------------------------
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty




------------------------------------
sudo lshw -c network
------------------------------------
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:fe500000-fe503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: d4:be:d9:9b:6c:ae
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:fe400000-fe40ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:18:85:2a:01:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-46-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11bgn




------------------------------------
ifconfig
------------------------------------
eth0      Link encap:Ethernet  HWaddr d4:be:d9:9b:6c:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30707 (30.7 KB)  TX bytes:30707 (30.7 KB)


wlan0     Link encap:Ethernet  HWaddr c0:18:85:2a:01:43  
          inet6 addr: fe80::c218:85ff:fe2a:143/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7974 (7.9 KB)  TX bytes:9330 (9.3 KB)




------------------------------------
rfkill list 
------------------------------------
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by mörgæs on 2015-03-11
If you remove the SOLVED flag there's a better chance of attracting help.
Also please edit the post above and add CODE tags around terminal output.

---

### Post by TheElder777 on 2015-03-11
> **mörgæs said:**
> If you remove the SOLVED flag there's a better chance of attracting help.
Also please edit the post above and add CODE tags around terminal output.
Thank you for the tips. I have done what you said.

---

### Post by Hadaka on 2015-03-11
you broke it again huh?  please do and post
```
lsmod | egrep 'wl | brcmsmac | bcma'
rfkill list all
```
thanks

---

### Post by TheElder777 on 2015-03-11
> **Hadaka said:**
> you broke it again huh?  please do and post
```
lsmod | egrep 'wl | brcmsmac | bcma'
rfkill list all
```
thanks

LOL. Yes, I broke it : ( 
I am at work. I will do this the first thing when I get home. Thank you for this, I'll reply today.

---

### Post by TheElder777 on 2015-03-11
> **Hadaka said:**
> you broke it again huh?  please do and post
```
lsmod | egrep 'wl | brcmsmac | bcma'
rfkill list all
```
thanks

Hey so I ran your commands in the terminal. The first command didn't return anything!?!? 
The second command (rfkill list all) returned the same thing in my latest code post:

```

0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no

```

---

### Post by wildmanne39 on 2015-03-13
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by TheElder777 on 2015-03-13
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks
THANK YOU FOR YOUR HELP AND REPLY!!!

I ran your script and followed the guides in the link but still no luck. Here is the output:

```


########## wireless info START ##########


Report from: 13 Mar 2015 19:30 PDT -0700


Booted last: 13 Mar 2015 19:27 PDT -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: tg3


##### lsusb #############################


Bus 002 Device 005: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 004: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 002 Device 003: ID 413c:2112 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              630669  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211
bcma                   52096  2 brcmsmac


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:fe9b:6cae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:549167 (549.1 KB)  TX bytes:208880 (208.8 KB)
          Interrupt:19 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::c218:85ff:fe2a:143/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5832 (5.8 KB)  TX bytes:7752 (7.7 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search gateway.pace.com


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Casa Villalobos: Infra, <MAC 'Casa Villalobos' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Polihale:        Infra, <MAC 'Polihale' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    Bolander:        Infra, <MAC 'Bolander' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    2WIRE293:        Infra, <MAC '2WIRE293' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    PS4-083AF4139BAF:Infra, <MAC 'PS4-083AF4139BAF' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    HOME548:         Infra, <MAC 'HOME548' [AC3]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    2WIRE458:        Infra, <MAC '2WIRE458' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    2WIRE536:        Infra, <MAC '2WIRE536' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    MotherOfDragons: Infra, <MAC 'MotherOfDragons' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    ATT996:          Infra, <MAC 'ATT996' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    RUSS 74:         Infra, <MAC 'RUSS 74' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    ATT8y9J8x5:      Infra, <MAC 'ATT8y9J8x5' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    NETGEAR83:       Infra, <MAC 'NETGEAR83' [AC16]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    ATT6j7B2H6:      Infra, <MAC 'ATT6j7B2H6' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Redsox26:        Infra, <MAC 'Redsox26' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    MRosales:        Infra, <MAC 'MRosales' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    2WIRE089:        Infra, <MAC '2WIRE089' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ATTwSTrxPi:      Infra, <MAC 'ATTwSTrxPi' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    pochacco:        Infra, <MAC 'pochacco' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    bunkie:          Infra, <MAC 'bunkie' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    2WIRE710:        Infra, <MAC '2WIRE710' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE882:        Infra, <MAC '2WIRE882' [AC11]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/ATT996]] (600 root)
[connection] id=ATT996 | type=802-11-wireless
[802-11-wireless] ssid=ATT996 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### iwlist scan #######################


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC '2WIRE293' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"2WIRE293"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008be0032b
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '2WIRE536' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"2WIRE536"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c3d6706
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME548' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HOME548"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000316000a7b
                    Extra: Last beacon: 13140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ATT996' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"ATT996"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001e164a04
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '2WIRE458' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE458"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019cd873420d
                    Extra: Last beacon: 644ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Bolander' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Bolander"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022a2d870b5
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'PS4-083AF4139BAF' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"PS4-083AF4139BAF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c018ea8b
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Polihale' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Polihale"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c2b7728cb
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Casa Villalobos' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Casa Villalobos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000376ccb9108
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Redsox26' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Redsox26"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000035d1f2c04c
                    Extra: Last beacon: 560ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '2WIRE882' [AC11]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"2WIRE882"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005372c6043e9
                    Extra: Last beacon: 12404ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'MotherOfDragons' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MotherOfDragons"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006b513793a8f
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Shay' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Shay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003f640813185
                    Extra: Last beacon: 13188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'RUSS 74' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"RUSS 74"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000269ab877146
                    Extra: Last beacon: 276ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'DIRECT-roku-206-90C3BC' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-206-90C3BC"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010ebeacc2c
                    Extra: Last beacon: 12404ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'NETGEAR83' [AC16]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR83"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e492c4ed80
                    Extra: Last beacon: 712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'Broughie' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Broughie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ef7907219d
                    Extra: Last beacon: 420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'ATT6j7B2H6' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ATT6j7B2H6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c8176af4b
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'MRosales' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MRosales"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001621b8d580c
                    Extra: Last beacon: 20ms ago


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     8A64A0EA2502AA6E237B856
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist ssb


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[    2.338629] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    2.339090] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    2.339682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   23.940129] wlan0: authenticate with <MAC 'ATT996' [AC4]>
[   23.941838] wlan0: send auth to <MAC 'ATT996' [AC4]> (try 1/3)
[   23.943360] wlan0: authenticated
[   23.947236] wlan0: associate with <MAC 'ATT996' [AC4]> (try 1/3)
[   23.950263] wlan0: RX AssocResp from <MAC 'ATT996' [AC4]> (capab=0x411 status=0 aid=4)
[   23.951605] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   23.951608] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   23.951615] wlan0: associated
[   23.951624] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.998950] wlan0: deauthenticating from <MAC 'ATT996' [AC4]> by local choice (reason=3)
[   57.004416] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   57.004420] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-03-14
Let's try the driver brcmsmac backported from kernel version 3.18. 

Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)
Right click and select Extract here. 
Then do:

```
sudo apt-get update
```
```
sudo apt-get install linux-headers-generic build-essential
```

```
cd ~/Desktop/backports-3.18-1
make defconfig-brcmsmac
make
sudo make install
```

Reboot

---

### Post by TheElder777 on 2015-03-14
> **Wild Man said:**
> Let's try the driver brcmsmac backported from kernel version 3.18. 

Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)
Right click and select Extract here. 
Then do:

```
sudo apt-get update
```
```
sudo apt-get install linux-headers-generic build-essential
```

```
cd ~/Desktop/backports-3.18-1
make defconfig-brcmsmac
make
sudo make install
```

Reboot

I did the above but unfortunately it didn't work : (  Anything else in mind? 

Thanks again for your help. I really have no idea how to fix this.

---

### Post by wildmanne39 on 2015-03-14
Run the wireless script again and post a new file so we can see what your connection is doing now with the new driver.
Thanks

---

### Post by TheElder777 on 2015-03-14
> **Wild Man said:**
> Run the wireless script again and post a new file so we can see what your connection is doing now with the new driver.
Thanks

Here it is:
```


########## wireless info START ##########


Report from: 14 Mar 2015 12:50 PDT -0700


Booted last: 14 Mar 2015 11:58 PDT -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: tg3


##### lsusb #############################


Bus 002 Device 005: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 004: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 002 Device 003: ID 413c:2112 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


brcmsmac              535019  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
mac80211              519760  1 brcmsmac
cfg80211              504836  2 brcmsmac,mac80211
bcma                   51815  2 brcmsmac
compat                 15137  4 bcma,cfg80211,brcmsmac,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:fe9b:6cae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2943668 (2.9 MB)  TX bytes:359056 (359.0 KB)
          Interrupt:19 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::c218:85ff:fe2a:143/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7142 (7.1 KB)  TX bytes:8143 (8.1 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search gateway.pace.com


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Casa Villalobos: Infra, <MAC 'Casa Villalobos' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA2
    Bolander:        Infra, <MAC 'Bolander' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    Polihale:        Infra, <MAC 'Polihale' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    2WIRE458:        Infra, <MAC '2WIRE458' [AC10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    HOME548:         Infra, <MAC 'HOME548' [AC6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    2WIRE536:        Infra, <MAC '2WIRE536' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    2WIRE293:        Infra, <MAC '2WIRE293' [AC8]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    RUSS 74:         Infra, <MAC 'RUSS 74' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    MotherOfDragons: Infra, <MAC 'MotherOfDragons' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    NETGEAR83:       Infra, <MAC 'NETGEAR83' [AN10]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Broughie:        Infra, <MAC 'Broughie' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Redsox26:        Infra, <MAC 'Redsox26' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    ATT996:          Infra, <MAC 'ATT996' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    My2WIRE394:      Infra, <MAC 'My2WIRE394' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    2WIRE882:        Infra, <MAC '2WIRE882' [AN15]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WPA
    2WIRE610:        Infra, <MAC '2WIRE610' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Shay:            Infra, <MAC 'Shay' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ATT6j7B2H6:      Infra, <MAC 'ATT6j7B2H6' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    DIRECT-roku-206-90C3BC: Infra, <MAC 'DIRECT-roku-206-90C3BC' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    2WIRE089:        Infra, <MAC '2WIRE089' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    MRosales:        Infra, <MAC 'MRosales' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    ATT8y9J8x5:      Infra, <MAC 'ATT8y9J8x5' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    2WIRE475:        Infra, <MAC '2WIRE475' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/ATT996]] (600 root)
[connection] id=ATT996 | type=802-11-wireless
[802-11-wireless] ssid=ATT996 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      5   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ATT996' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"ATT996"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d120a9bc
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Bolander' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Bolander"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003126d56a63
                    Extra: Last beacon: 440ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Casa Villalobos' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Casa Villalobos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000045f359f002
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Polihale' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Polihale"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ab20da257
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '2WIRE536' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"2WIRE536"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000aa172fd
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HOME548' [AC6]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"HOME548"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000119f41ff54
                    Extra: Last beacon: 588ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'MotherOfDragons' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MotherOfDragons"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006c39a0beac4
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '2WIRE293' [AC8]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"2WIRE293"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000078b84f1
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'RUSS 74' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"RUSS 74"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002783213e1ac
                    Extra: Last beacon: 360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '2WIRE458' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"2WIRE458"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ab5fb5382c
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'MRosales' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MRosales"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000170a21ce522
                    Extra: Last beacon: 16ms ago
          Cell 12 - Address: <MAC 'My2WIRE394' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"My2WIRE394"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f22e47181
                    Extra: Last beacon: 664ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Broughie' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Broughie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fdff93918c
                    Extra: Last beacon: 496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'DIRECT-roku-206-90C3BC' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-206-90C3BC"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f733e31c2
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '#GetoffMyShit' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"#GetoffMyShit"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001036e2a46a7
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     16D0F2223895D565D1F0F05
depends:        bcma,mac80211,compat,brcmutil,cfg80211,cordic
vermagic:       3.13.0-46-generic SMP mod_unload modversions 


[brcmutil]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A0783053E3D218C552A3D06
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.13.0-46-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
srcversion:     67A85C25BB329C2FD4C350A
depends:        cfg80211,compat
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     3423C785282C0C62D3BEBB4
depends:        compat
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/bcma/bcma.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     A1F6002F0A36A4D16AEFF24
depends:        compat
vermagic:       3.13.0-46-generic SMP mod_unload modversions 


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist ssb


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[    2.580868] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    2.581367] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[    2.581982] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   28.824758] wlan0: authenticate with <MAC 'ATT996' [AC1]>
[   28.824764] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   28.824802] wlan0: send auth to <MAC 'ATT996' [AC1]> (try 1/3)
[   28.845012] wlan0: authenticated
[   28.845391] wlan0: associate with <MAC 'ATT996' [AC1]> (try 1/3)
[   28.850114] wlan0: RX AssocResp from <MAC 'ATT996' [AC1]> (capab=0x411 status=0 aid=2)
[   28.850727] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[   28.850730] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   28.850736] wlan0: associated
[   28.850752] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.247946] wlan0: deauthenticating from <MAC 'ATT996' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   74.249895] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   74.249903] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-03-14
Go into your router configuration and change encryption to just WPA2 (AES) (CCMP) do not use (TKIP).
Make sure to disable ethernet connection before trying to connect to wifi.

Delete all notworks from network manager and reboot then go into network manager top right corner of the screen and click on edit connection then wirelesss and set IPV6 to ignore.

If it does not connect run:
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Edit:
In your router there is a drop down with  HT/VHT see if you can enable that.
reboot.

---

### Post by TheElder777 on 2015-03-14
> **Wild Man said:**
> Go into your router configuration and change encryption to just WPA2 (AES) (CCMP) do not use (TKIP).
Make sure to disable ethernet connection before trying to connect to wifi.

Delete all notworks from network manager and reboot then go into network manager top right corner of the screen and click on edit connection then wirelesss and set IPV6 to ignore.

If it does not connect run:
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Edit:
In your router there is a drop down with  HT/VHT see if you can enable that.
reboot.
Thank you for your time. 

I configured my router as you said. I then deleted my networks and rebooted. I couldn't set IPv6 to ignore because I deleted my network from the manager. So i had to add it again THEN set IPv6 to ignore. I don't know if that matters, but just letting you know. Rebooted and tried again (this is without my Ethernet cable plugged in). It didnt work. 

I then ran the command in terminal and rebooted... Still, nothing : (

I wonder if it is from the latest ubuntu patch/update. I also wonder if there is a way to remove the latest updates that installed. 

Please tell me you have a alternative approach?!?

Thanks again for your priceless help...

---

### Post by Hadaka on 2015-03-14
Hi, Let's boot you up to an eariler linux  version and see what happens.

remove the ethernet cable
power down the computer
power up the computer while holding down the shift key
choose " Select a Previous Linux version"
#you last had it working aug. 2014..pick one after the aug 2014 date
boot to the older version and report back
tthanks.

---

### Post by TheElder777 on 2015-03-14
> **Hadaka said:**
> Hi, Let's boot you up to an eariler linux  version and see what happens.

remove the ethernet cable
power down the computer
power up the computer while holding down the shift key
choose " Select a Previous Linux version"
#you last had it working aug. 2014..pick one after the aug 2014 date
boot to the older version and report back
tthanks.

I tried holding down shift while booting but i didn't get anything...

Also, i'm not sure what you mean by "last had it working aug 2014," if you are speaking of my wifi internet, that was working a 5 days ago or so.

Thank you for your help.

---

### Post by Hadaka on 2015-03-14
ok, s o leave the ethernet cable in then, try quickly tapping the
shift key as is boots up. this is how you get in the recovery mode...the grub menu
so keep trying different things untill you do. 5 days ago??? ok..so what exactly were
you doing when it stopped working???

---

### Post by Easy Limits on 2015-03-15
Hi,

This worked for me on 12.04 on an old P4 laptop.

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by TheElder777 on 2015-03-19
> **Hadaka said:**
> ok, s o leave the ethernet cable in then, try quickly tapping the
shift key as is boots up. this is how you get in the recovery mode...the grub menu
so keep trying different things untill you do. 5 days ago??? ok..so what exactly were
you doing when it stopped working???

Hey! Sorry for the late reply. I had finals. I was able to get grub, i then loaded the oldest version. I was not able to log in (my screen would freeze or something) but i was able to play with wireless from the log in screen. It still had the same problem. So i guess it isn't the update. I may have been wrong. 

Yes, 5 days ago. What I was doing was trying to set up a static ip but i then went back to automatic (did all this from the network gui, i wonder if permanently changed my networking files...) . I also got a new laptop that started connecting to the network. I dont know if these had something to do with the issue, but this is what i was doing.

---

### Post by TheElder777 on 2015-03-21
hello again. I apologize for all these posts but i still don't have wifi on my desktop computer and it is starting to get really annoying. I hate having to reinstall ubuntu to fix a small issue like this. I have been trying to get it fixed. I now get the following from lshw:

```

ASDFASDFADSF:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: d4:be:e9:9b:6c:ae
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:fe400000-fe40ffff

```

Here is what i get after i load bcmsmac using modprobe

```

ASDFASDFADSF:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:fe500000-fe503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: d4:be:e9:9b:6c:ae
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=sb ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 memory:fe400000-fe40ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:18:85:2a:01:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-46-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11bgn

```
After I reboot my computer (and after having modprobed bcmsmac) I have to modprobe it again (after every reboot)... I don't care for this now since even after modprobing it my wifi still doesn't work (even after driver is shown in lshw [like above]). 

here is my blacklist.conf file:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
#blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
#blacklist bcma

```


I feel I am close. I installed bcmwl using apt-get. I am trying to load my driver (bcmwl) and modprobe it but I am having problems. Can anyone help please... !!!
If I can't get it to work i will reinstall ubuntu (and let the sense of defeat wash over me).

---

### Post by TheElder777 on 2015-03-21
I got it to work!!! I had my Gateway set to WPA TKIP and I needed to have it at WPA TKIP/WPA2 AES! I had played with that setting earlier. I should have figured this out earlier. Thank you all for your wonderful help and time. Sorry for the multiple posts and for resurrecting this thread.

I still have one final minor issue. I have to modprobe brcmsmac after every reboot. How can I have this be automated?

EDIT:

Final issue fixed with the following link:   [http://ubuntuforums.org/showthread.php?t=1938217](http://ubuntuforums.org/showthread.php?t=1938217)
Lesson learned: If you had played with your router/gateway settings earlier, try to revert to see if that fixes it before assuming something is wrong with your computer. 

Thanks again for the very helpful people and sorry for taking your time.

---

