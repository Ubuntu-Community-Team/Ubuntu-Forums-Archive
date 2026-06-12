---
title: "strange server networking problems"
date: 2017-03-17
forum: Networking &amp; Wireless
---

### Post by alving on 2017-03-17
hello

i have a hi-speed network set up in the house. 2 (gaming) computers are wired the other (netflix) uses wifi
as well as numerous cell phones and tablets.

im trying to set up an Edubuntu 14.04.5 LTSP network with its own router.
i have a 32 bit server and 2 i386 systems that all works, no problems yet.

my LTSP server connects to the home network by wifi (usb adapter), and is connected to the 2nd (LTSP) router by wire via onboard lan port.
when the wired connection is enabled through the network-manager i have no internet access on server.

the problem is...      how do i go about setting up the server so that:
i have full internet access on the server?
the clients have full access to the software center, updates & upgrades?     NO other internet access.

i know this would be much easier if i connect the 2 router with a cable, or add a network card to the server.
i just dont want any more cables running around the house...

is there a way to connect the 2 routers through wifi?

i dont have any idea what info would be most relevant. heres a start.

/etc/network/interfaces - ive googled and edited this file so many times. and now im right back where i started, with no luck at all.
currnetly it is:
auto lo
iface lo inet loopback


THE FOLLOWING INFO IS WITH THE ONBOARD LAN DISABLED...

```
papa@LTSP32:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 00:13:8f:0c:3b:82 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether c8:3a:35:c1:38:79 brd ff:ff:ff:ff:ff:ff

papa@LTSP32:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Rogers20248"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:B6:FC:3E:46:58   
          Bit Rate=57.8 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS th:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:706   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

papa@LTSP32:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:0c:3b:82  
          inet6 addr: fe80::213:8fff:fe0c:3b82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:858212 (858.2 KB)  TX bytes:243656 (243.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:281158 (281.1 KB)  TX bytes:281158 (281.1 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c1:38:79  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2607:fea8:1ca0:8e9:ca3a:35ff:fec1:3879/64 Scope:Global
          inet6 addr: fe80::ca3a:35ff:fec1:3879/64 Scope:Link
          inet6 addr: 2607:fea8:1ca0:8e9:212b:b869:cd4c:7f42/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2136229 (2.1 MB)  TX bytes:1247762 (1.2 MB)


papa@LTSP32:~$ sudo lshw:

-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:0c:3b:82
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:e800(size=256) memory:ff6ffc00-ff6ffcff

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: c8:3a:35:c1:38:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-66-generic firmware=0.29 ip=192.168.0.17 link=yes multicast=yes wireless=IEEE 802.11bgn
```

please help.
i will reply to this post shortly with the info for when wired connection is enabled.

thanks in advance
any thoughts will be greatly appreciated.

speaking of which...
the wire wasnt connected to the computer when i did this install.
i set up the LTSP wired network after i made sure the server was working properly.
i didnt have the wifi adapter plugged in while setting up it up either.
should i just do another full install with wire and wifi connected?

---

### Post by wildmanne39 on 2017-03-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by alving on 2017-03-17
thanks for refreshing me, i did know how. but, im a regular reader and havent post for quite a while.

---

### Post by alving on 2017-03-17
ok. heres the same output as above.
except this time the onboard lan is enabled.

```

papa@LTSP32:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether 00:13:8f:0c:3b:82 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether c8:3a:35:c1:38:79 brd ff:ff:ff:ff:ff:ff

papa@LTSP32:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Rogers20248"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:B6:FC:3E:46:58   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

papa@LTSP32:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:0c:3b:82  
          inet addr:192.168.0.51  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe0c:3b82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22394 (22.3 KB)  TX bytes:35660 (35.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:26690 (26.6 KB)  TX bytes:26690 (26.6 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c1:38:79  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2607:fea8:1ca0:8e9:ca3a:35ff:fec1:3879/64 Scope:Global
          inet6 addr: 2607:fea8:1ca0:8e9:4872:5c47:337b:1c3a/64 Scope:Global
          inet6 addr: fe80::ca3a:35ff:fec1:3879/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11176 (11.1 KB)  TX bytes:12890 (12.8 KB)

papa@LTSP32:~$ sudo lshw

        *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:0c:3b:82
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=192.168.0.51 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:e800(size=256) memory:ff6ffc00-ff6ffcff


  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: c8:3a:35:c1:38:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-66-generic firmware=0.29 ip=192.168.0.17 link=yes multicast=yes wireless=IEEE 802.11bgn

```

i havent checked the difference between these 2 outputs yet.
but, im pretty sure what they are.

i just dont know what i can to do to fix it.

EDIT:
i completely forgot about the router info

home network:
router is cgn2-rog
address 192.168.0.1
netmask 255.255.254.0
dhcp host enabled, range 192.168.0.1 - 192.168.199
wifi is enabled

LTSP network:
router is D-Link dir-601???
address 192.168.0.50
netmask 255.255.255.0
dhcp host enabled, range 192.168.0.51 - 192.168.0.100
wifi is disabled


just had another thought.
going to shutdown
disconnect the hard drive, hook up a little 40 Gig i have lying around.
then try to install while everything is connected.
.

---

### Post by alving on 2017-03-18
ok.   did fresh install on 40Gb with worst results yet.

both wifi and lan connections were detected during install. wifi used to install updates during install.
neither worked after.

same commands as above:

```

papa@LTSP32:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:13:8f:0c:3b:82 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether c8:3a:35:c1:38:79 brd ff:ff:ff:ff:ff:ff

papa@LTSP32:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Rogers20248"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:B6:FC:3E:46:58   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:71   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

papa@LTSP32:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:0c:3b:82  
          inet addr:192.168.0.51  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:30988 (30.9 KB)  TX bytes:30988 (30.9 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c1:38:79  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2607:fea8:1ca0:8e9:ca3a:35ff:fec1:3879/64 Scope:Global
          inet6 addr: 2607:fea8:1ca0:8e9:18c6:137c:ea1e:6891/64 Scope:Global
          inet6 addr: fe80::ca3a:35ff:fec1:3879/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38442 (38.4 KB)  TX bytes:16931 (16.9 KB)

papa@LTSP32:~$ sudo lshw

        *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:0c:3b:82
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=half ip=192.168.0.51 latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:e800(size=256) memory:ff6ffc00-ff6ffcff

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: c8:3a:35:c1:38:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-31-generic firmware=0.29 ip=192.168.0.17 link=yes multicast=yes wireless=IEEE 802.11bgn

```

i think ive fixed part of my problem.
the d-link router is no longer set up to be dhcp host.
ive plugged the network cable from server to lan port of router.

i currently cant access the d-link router, going to disable the wifi and try again.

thanks again

---

### Post by alving on 2017-03-19
hey all.

unfortunately ive had a component failure in a system with higher priorities.

my intention is get this project up and running some day.

unfortunately, it dont see it being any time soon.


thanks
alving

---

