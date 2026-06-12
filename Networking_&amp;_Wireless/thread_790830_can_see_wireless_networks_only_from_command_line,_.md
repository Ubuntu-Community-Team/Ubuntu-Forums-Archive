---
title: "can see wireless networks only from command line, can't connect"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by raquis on 2008-05-11
I'm a newbe using an HP Omnibook 4150 with an Airlink wireless card which has an Atheros AR5212/5213 device. Running Ubuntu 8.04. The edit wireless network GUI doesn't show anything alive and I can't get it to talk to my network.

system>administration>network looked at wireless connection properties, brings up a window titled ath0 properties but everything grayed out. edit wireless networks from right click on network icon shows no devices or detected networks.

Some info about configuration:
some was abriveated to show pertinent info only.
iwconfig
iwlist scan
ifconfig
lshw

russq@ubuntu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"quisnet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:A3:1F:35:FA   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-52 dBm  Noise level=-93 dBm
          Rx invalid nwid:190040  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

russq@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:A3:1F:35:FA
                    ESSID:"quisnet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100070100
           ... 

russq@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:e8:d2:55  
          inet6 addr: fe80::211:95ff:fee8:d255/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28 (28.0 B)  TX bytes:342 (342.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:11:95:e8:d2:55  
          inet addr:169.254.8.229  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43616 (42.5 KB)  TX bytes:43616 (42.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-E8-D2-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:385719 errors:0 dropped:0 overruns:0 frame:200265
          TX packets:50101 errors:74 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:41898839 (39.9 MB)  TX bytes:2642854 (2.5 MB)
          Interrupt:10 

russq@ubuntu:~$ lshw
           ...
     *-network
          description: Wireless interface
          product: AR5212/AR5213 Multiprotocol MAC/baseband processor
          vendor: Atheros Communications Inc.
          physical id: 0
          bus info: pci@0000:06:00.0
          logical name: wifi0
          version: 01
          serial: 00:11:95:e8:d2:55
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

followed steps at [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo). Tried [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).

commands that I ran to attempt setup (not in this order):
sudo iwconfig ath0 essid "quisnet"
sudo iwconfig ath0 ap 00:0f:a3:1f:35:fa
sudo iwconfig ath0 key s:<MyKey>[2]    // note second key
sudo iwpriv ath0 authmode 2                  // shared encryption key
sudo iwconfig ath0 commit
  returned:
  Error for wireless request "Commit changes" (8B00) :
        SET failed on device ath0 ; Operation not supported.
sudo dhclient ath0
  returned:
  ...
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

ping local loopback device successful
ping -c 4 127.0.0.1
ping wireless router failed
ping -c 4 192.168.0.11

In summary, the atheros device appears to be detected by the OS, it appears to detect networks from command line but not from GUI. It doesn't connect or send at all.

I'm running out of posts to resolve problem with no success. Any insight would be appreciated.

---

### Post by lswest on 2008-05-11
try doing it like this:
```
sudo iwconfig ath0 essid "quisnet" ap 00:0f:a3:1f:35:fa key s:<MyKey>[2] && sudo dhclient ath0
``` by default the key will be seen as "shared" unless marked as restricted.

however, what confuses me is that your lshw output lists the interace as wifi0 with the right drivers, and then no mention of the ath0 device, and the wifi0 has no scan output.

---

### Post by pro003 on 2008-05-11
try this in terminal:

```

sudo ifconfig ath0 up

sudo ifconfig wifi0 up

sudo ifconfig eth0 down

sudo ifconfig ath0 up
```

then

```
ifconfig
```

and post the output here...

---

### Post by raquis on 2008-05-11
Thank you Iswest and pro003 for your replys.

Iswest,

Results of your suggestion are as follows:

russq@ubuntu:~$ sudo iwconfig ath0 essid "quisnet" ap 00:0f:a3:1f:35:fa key s:*************[2] && sudo dhclient ath0
[sudo] password for russq: 
There is already a pid file /var/run/dhclient.pid with pid 5425
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e8:d2:55
Sending on   LPF/ath0/00:11:95:e8:d2:55
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

russq@ubuntu:~$ 



pro003,

The ifconfig output that you requested is below. Note eth0 device  got an error.

russq@ubuntu:~$ sudo ifconfig ath0 up
russq@ubuntu:~$ sudo ifconfig wifi0 up
russq@ubuntu:~$ sudo ifconfig eth0 down
eth0: ERROR while getting interface flags: No such device
russq@ubuntu:~$ sudo ifconfig ath0 up
russq@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:e8:d2:55  
          inet6 addr: fe80::211:95ff:fee8:d255/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:11:95:e8:d2:55  
          inet addr:169.254.8.229  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35484 (34.6 KB)  TX bytes:35484 (34.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-E8-D2-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620416 errors:0 dropped:0 overruns:0 frame:296768
          TX packets:71831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:67340648 (64.2 MB)  TX bytes:3846080 (3.6 MB)
          Interrupt:10 

russq@ubuntu:~$

---

### Post by lswest on 2008-05-12
hmm, could you maybe post back the results of ```
lshw -C network
``` of the device whose logical name is ath0?  that's the card we need to look at, not sure how it works with madwifi though.

Also, that tutorial looks quite old, don't know (since i don't have an atheros card) if the process has been updated, but maybe someone else will know.  See if you can find a more up to date how-to, and then compare the processes, maybe there's a newer way to do it?

---

### Post by raquis on 2008-05-12
Thanks again lswest. The response is:

russq@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:e8:d2:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
russq@ubuntu:~$

---

### Post by lswest on 2008-05-12
ah, sorry about making you post the same thing twice, i've never had an atheros card, but i was looking through this thread: [http://ubuntuforums.org/showthread.php?t=722798](http://ubuntuforums.org/showthread.php?t=722798) and i was wondering, have you tried ```
sudo dhclient -r ath0
``` or else maybe just have a look through that thread, seems to be the same card as yours.

---

### Post by raquis on 2008-05-13
Thanks for the suggestion, lswest. I tried everything in the link that you suggested but it was mostly stuff that I tried already. I also have the difference that I can see networks from "iwlist scan". The output that I got from "sudo dhclient -r ath0" was:

russq@ubuntu:~$ sudo dhclient -r ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:e8:d2:55
Sending on   LPF/ath0/00:11:95:e8:d2:55
Sending on   Socket/fallback
russq@ubuntu:~$ 

So the mystery continues. I've been studying madwifi at this end as time allows. I've seen configuration files in other areas. I wonder if there could be one here with a problem statement?

Thanks again

---

### Post by raquis on 2008-05-18
To anyone that followed the thread to the end, here's what finally fixed it.

I booted the computer (HP Omnibook 4150 laptop) with the wireless lan pcmcia card removed. After logging in I hotplugged the card. It found the card and network manager recognized it.

Thanks again for the suggestions received here.

---

