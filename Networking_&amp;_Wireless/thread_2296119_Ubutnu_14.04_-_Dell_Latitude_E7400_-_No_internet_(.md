---
title: "Ubutnu 14.04 - Dell Latitude E7400 - No internet (shows connection)"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by Nitay_Kufert on 2015-09-23
Hey, as the title describes - it shows as if i am connected but i cant, for example, ping [www.google.com]("http://www.google.com").

I saw lots of problems while searching around the forum regarding Broadcom drivers -  but it doesn't seem to be the case for me (my wifi and Ethernet  drivers are not Broadcom).

I ran the wireless-info on the problematic machine but i can't share all of its content with you as this is a work computer. ill share what i think is a good starting point and will supply what you ask :)

##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Dell Device [1028:05cb]
    Kernel driver in use: e1000e


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 031: ID 413c:81a3 Dell Computer Corp. 
Bus 002 Device 002: ID 0c45:64d2 Microdia 
Bus 002 Device 032: ID 0781:5530 SanDisk Corp. Cruzer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Additional info:
While i am at work - i don't have any problem using the internet, and everything works fine. Its only happening with other networks (I tried connecting to 2 different networks so far - and same problem)

Let me know if you miss some crucial information,
Thanks anyway!

Nitay

---

### Post by chili555 on 2015-09-24
> While i am at work - i don't have any problem using the internet, and everything works fine. Its only happening with other networksDo you mean wired or wireless or both? May we concentrate on one or the other first? May we see:```
ifconfig
iwconfig
route -n
```Thanks.

---

### Post by Nitay_Kufert on 2015-09-24
Thanks for your reply!

The problems happens both on wired and wireless connection on networks outside my work,
and while i am at work i can connect both with the wired and wireless connection with no problems.

#### ifconfig ####

docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99            inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::5484:7aff:fefe:9799/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1155460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:563554628 (563.5 MB)  TX bytes:2618722168 (2.6 GB)


eth0      Link encap:Ethernet  HWaddr f0:1f:af:55:74:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10314974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4726434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9714343727 (9.7 GB)  TX bytes:885460549 (885.4 MB)
          Interrupt:20 Memory:f7e00000-f7e20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:138667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23457693 (23.4 MB)  TX bytes:23457693 (23.4 MB)


veth0208698 Link encap:Ethernet  HWaddr b2:21:b8:92:fa:b0  
          inet6 addr: fe80::b021:b8ff:fe92:fab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1155460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:579731068 (579.7 MB)  TX bytes:2618735262 (2.6 GB)


wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:98:0d:af  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e8b:fdff:fe98:daf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1753304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221297974 (221.2 MB)  TX bytes:6160886 (6.1 MB)

#### iwconfig ####

wwan0     no wireless extensions.

veth0208698  no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Nitay o_O"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0E:F4:DD:FA:61   
          Bit Rate=270 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0


docker0   no wireless extensions.

#### route -n ####

Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

---

### Post by chili555 on 2015-09-24
It appears this is a Docker installation over a host operating system. I am unfamiliar with such things. I haven't any other suggestions.

---

### Post by Nitay_Kufert on 2015-09-25
I don't think the docker has anything to do with it - but i will try and work around it and test again.
Thanks anyway! 

Anyone else?

---

### Post by Nitay_Kufert on 2015-10-03
```
sudo dpkg-reconfigure resolvconf
```
Solved my problem - i had bad configuration

---

