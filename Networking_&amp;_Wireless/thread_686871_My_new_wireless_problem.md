---
title: "My new wireless problem"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by 786souljah on 2008-02-03
Hello,

I installed my usb wireless adapter (D-Link WUA-1340) and have hooked up a network with my windows computer. The router being used is old but should work? (D-Link DI-514).

Heres the issue:

The usb device scans correctly and finds the network i have set up. The SSID is correct and all things function as they should till now. I start to connect the network however this is where the problem occurs. At times, (only once so far) it connected and showed a 75% connection to the network. Only problem here was i opened firefox and nothing would load. Not even a simple page like google. All the other times, all i get is one green light (instead of 2) at the top menu bar showing status of connectivity.

What might the problem here be? Ive tried everything from using WEP keys (which ubuntu does recognize and a dialog box pops up asking for the key) to leaving an insecure connection without any incription and no password. What should i do?

Thank you for all your help, i might be missing something but im completely new to linux so still adapting. Thanks again,

-Alim

---

### Post by wieman01 on 2008-02-04
Once you have established a connection, please post this:
> route
> sudo iwlist scan
> sudo iwconfig
> sudo lshw -C network
So you are basically saying that you are connected but cannot browse the web? What chipset is your wireless adapter?

---

### Post by ohioiom on 2008-02-04
Hello wieman01,
I have been trawling the forum for the answer to a similar problem to 786souljah. I have Ubuntu 7.10 installed on my laptop dual booting with WinXP Pro.
If I use my Belkin dongle I am fully on line 100% as I am at the moment, but if I use my BT Voyager 1065 PCI card I can only get a signal of anything from 60-80%, which is insufficient to get on line, also, using the PCI card  seems to effect the way the programme restarts or shuts down, it goes through a lot of data and then freezes and I have to switch it off by holding the on/off switch down. When I use the dongle everything works fine. I noted the info. you asked to provide, so I looked for it on my Laptop, while using the PCI card, here it is:-
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
                    Quality=93/100  Signal level=-40 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 116ms ago

peter@peter-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"BTHomeHub-8CE9"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:F6:76:A2:93   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:57C7-FCC1-51   Security mode:open
          Link Quality=65/100  Signal level=-50 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:22  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@peter-laptop:~$ sudo ishw-C network
sudo: ishw-C: command not found
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
I would prefer to use the PCI card as it is less vunerable to getting knocked.
Hope this info. is helpful in solving the problem, please bear in mind I am a newbie and Stupid People language would help.
Many thanks
Peter

---

### Post by wieman01 on 2008-02-04
> **ohioiom said:**
> Hello wieman01,
I have been trawling the forum for the answer to a similar problem to 786souljah. I have Ubuntu 7.10 installed on my laptop dual booting with WinXP Pro.
If I use my Belkin dongle I am fully on line 100% as I am at the moment, but if I use my BT Voyager 1065 PCI card I can only get a signal of anything from 60-80%, which is insufficient to get on line, also, using the PCI card  seems to effect the way the programme restarts or shuts down, it goes through a lot of data and then freezes and I have to switch it off by holding the on/off switch down. When I use the dongle everything works fine. I noted the info. you asked to provide, so I looked for it on my Laptop, while using the PCI card, here it is:-
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
                    Quality=93/100  Signal level=-40 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 116ms ago

peter@peter-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"BTHomeHub-8CE9"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:F6:76:A2:93   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:57C7-FCC1-51   Security mode:open
          Link Quality=65/100  Signal level=-50 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:22  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@peter-laptop:~$ sudo ishw-C network
sudo: ishw-C: command not found
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
I would prefer to use the PCI card as it is less vunerable to getting knocked.
Hope this info. is helpful in solving the problem, please bear in mind I am a newbie and Stupid People language would help.
Many thanks
Peter
Hello Peter, 

Hijacking threads isn't considered the politest thing in this forum. Please open up your own thread and feel free to send me the link to it by PM. I'll help, but starting from another thread please.

---

