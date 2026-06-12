---
title: "PCI wireless problems"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by ohioiom on 2008-02-04
Hello wieman01,
First of all, I would like to apologise to you and to the forum for my indiscretetion, ie. hijacking another member's thread.
I have been trawling the forum for the answer to a similar problem to 786souljah. I have Ubuntu 7.10 installed on my laptop dual booting with WinXP Pro.
If I use my Belkin dongle I am fully on line 100% as I am at the moment, but if I use my BT Voyager 1065 PCI card I can only get a signal of anything from 60-80%, which is insufficient to get on line, also, using the PCI card seems to effect the way the programme restarts or shuts down, it goes through a lot of data and then freezes and I have to switch it off by holding the on/off switch down. When I use the dongle everything works fine. I noted the info. you asked to provide, so I looked for it on my Laptop, while using the PCI card, here it is:-
peter@peter-laptop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         api.home        0.0.0.0         UG    0      0        0 eth2
peter@peter-laptop:~$ sudo iwlist scan
[sudo] password for peter:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:18:F6:76:A2:93
                    ESSID:"BTHomeHub-8CE9"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-46 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 76ms ago
          Cell 02 - Address: 00:18:4D:3C:D2:64
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-81 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 336ms ago

peter@peter-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"BTHomeHub-8CE9"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:F6:76:A2:93   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:57C7-FCC1-51   Security mode:open
          Link Quality=58/100  Signal level=-54 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:4  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@peter-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:0d:02:63:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 02
       serial: 00:11:f5:c6:a8:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.1.70 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
peter@peter-laptop:~$ 

I would prefer to use the PCI card if atall possible, as it is less vunerable to getting knocked. Hope this info is helpful, if you need the read out for the dongle, please let me know.
Many thanks. Sorry about these smilies I do not know where they came from or how to get rid of them! 
Peter

---

### Post by wieman01 on 2008-02-04
I'll reply to you later on, gotta run. :-) But take a look at this thread, it will be helpful. Kevdog is very knowledge and I think we will be able to help you with combined effort.

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by ohioiom on 2008-02-05
Thanks wieman01,

In the meantime I will take a look at kevdog's post.

Before I do, some more info. My Laptop keyboard sometimes appears to be disconnected, I can type my name and password when starting up, but after that, I can't type anything in anywhere eg. Terminal, Notebook etc., and when I restart, I get a lot of data scrolling down and it finally stops at this:-  

 NetworkManager::  <info> Caught termination signal

NetWorkManager: <debug> [1202208835.023216] nm_print_open_socks( ): Open Sockets List:

NetworkManager: <debug> [1202208835.023480] nm_print_open_socks( ) : Open Sockets List Done

NetworkManager: <info> Deactivating device eth0
                                                                                                                                           [ OK ]

NetworkManager: <info> Deactivating device eth2

NetworkManager: <info> SUP: sending command 'DISABLE_NETWORK 0'

*Sending all processes the KILL signal...                                                                                [ OK ]
* Unmounting temporary filesystems                                                                                      [ OK ]
* Deactivating swap...                                                                                                           [ OK ]
* Unmounting local filesystems...
unmount2: No such file or directory
unmount: /media/windows040XP040Pro: not found                                                                  
                                                                                                                                          [[COLOR="Red"]fail[/COLOR]]

* Will now restart   

But it doesn't!!

Now it won't let me access any programmes, type anything or even activate 'Quit'
All I can activate is what I have on my desktop, 'Windows XP Pro' and 'photo folder' 

Peter

---

