---
title: "No DHCPOFFERS received by BCM4318 wireless card"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by gorbulas on 2007-03-10
I'm having terrible trouble trying to get my Broadcom wireless card on my laptop to work. Here is my hardware:
compaq presario v2000 laptop
Broadcom BCM4318 wireless card
DI-624+ wireless router
Ubuntu 6.10

Ok, so I've spend probably at least 10+ hours (over a few sessions, these last few months) scrolling the web trying to figure out why its not working. I've got ndiswrapper working:

```
matt@matt-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
```

It picks up the wireless signal, as wifi radar picks it up, but it never connects.

```
matt@matt-laptop:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:off/any  Nickname:"The Grindell Network"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
matt@matt-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:95:72:1B:52
                    ESSID:"The Grindell Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

```
matt@matt-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:14:A5:7F:4D:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:d0204000-d0206000
```

```
Mar 11 14:56:30 matt-laptop hcid[4353]: Bluetooth HCI daemon
Mar 11 14:56:30 matt-laptop hcid[4353]: Register path:/org/bluez fallback:1
Mar 11 14:56:30 matt-laptop dhclient: isc-dhclient-V3.0.4
Mar 11 14:56:30 matt-laptop sdpd[4364]: Bluetooth SDP daemon 
Mar 11 14:56:35 matt-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Mar 11 14:56:46 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Mar 11 14:56:51 matt-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Mar 11 14:56:51 matt-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 14:56:51 matt-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 14:56:51 matt-laptop dhclient: All rights reserved.
Mar 11 14:56:51 matt-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 11 14:56:51 matt-laptop dhclient: 
Mar 11 14:56:51 matt-laptop dhclient: Listening on LPF/eth0/00:16:36:23:37:9b
Mar 11 14:56:51 matt-laptop dhclient: Sending on   LPF/eth0/00:16:36:23:37:9b
Mar 11 14:56:51 matt-laptop dhclient: Listening on LPF/eth1/00:14:a5:7f:4d:42
Mar 11 14:56:51 matt-laptop dhclient: Sending on   LPF/eth1/00:14:a5:7f:4d:42
Mar 11 14:56:51 matt-laptop dhclient: Sending on   Socket/fallback
Mar 11 14:56:51 matt-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 14:56:51 matt-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 14:56:51 matt-laptop dhclient: All rights reserved.
Mar 11 14:56:51 matt-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 11 14:56:51 matt-laptop dhclient: 
Mar 11 14:56:52 matt-laptop dhclient: Listening on LPF/eth1/00:14:a5:7f:4d:42
Mar 11 14:56:52 matt-laptop dhclient: Sending on   LPF/eth1/00:14:a5:7f:4d:42
Mar 11 14:56:52 matt-laptop dhclient: Sending on   Socket/fallback
Mar 11 14:56:54 matt-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Mar 11 14:56:55 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 11 14:57:01 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Mar 11 14:57:03 matt-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Mar 11 14:57:03 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Mar 11 14:57:11 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 11 14:57:15 matt-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 14:57:18 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Mar 11 14:57:19 matt-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Mar 11 14:57:19 matt-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 11 14:57:20 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Mar 11 14:57:21 matt-laptop dhclient: No DHCPOFFERS received.
Mar 11 14:57:21 matt-laptop dhclient: No working leases in persistent database - sleeping.
Mar 11 14:57:21 matt-laptop ntpdate[4738]: can't find host ntp.ubuntu.com 
Mar 11 14:57:21 matt-laptop ntpdate[4738]: no servers can be used, exiting
Mar 11 14:57:23 matt-laptop dhclient: No DHCPOFFERS received.
Mar 11 14:57:23 matt-laptop dhclient: No working leases in persistent database - sleeping.
Mar 11 14:57:23 matt-laptop ntpdate[4755]: can't find host ntp.ubuntu.com 
Mar 11 14:57:23 matt-laptop ntpdate[4755]: no servers can be used, exiting
Mar 11 15:18:25 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar 11 15:18:29 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 11 15:18:38 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Mar 11 15:18:51 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 11 15:18:58 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 11 15:19:07 matt-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Mar 11 15:19:26 matt-laptop dhclient: No DHCPOFFERS received.
Mar 11 15:19:26 matt-laptop dhclient: No working leases in persistent database - sleeping.
```


As shown above in the daemon.log, it is not getting DHCPOFFER from the wireless router. I have tried setting up a static IP on both router and putting the setting into ubuntu, but that didn't work. Have also disabled WEP to see if that were the problem, but that didn't work either.

The wireless light flashes on the laptop steadily, but under windows XP, it normally is on all the time to signify the wireless card is on. Also note that I can access the internet fine, by plugging the laptop into the router via ethernet cable, but this is less than convenient.

Does anyone have any ideas? I haven't really found any solutions on google for this. Any help is very much appreciated.

---

### Post by gorbulas on 2007-03-10
Ok, does anyone know what this means? 

```
matt@matt-laptop:~$ sudo ndiswrapper -m
module configuration contains directive install pci:v000014E4d00004318sv00001468sd00000311bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004318sv00001468sd00000312bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004318sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive
```

I went into the folder /sbin/ and found a number of files with broken links, and it won't let me send them to the trash, specifically these files: 
kallsyms, ksyms, lsmod.modutils, modprobe.modutils, rmmod.modutils
Would that have anything to do with it?

---

### Post by Floppyjoe on 2007-03-11
I noticed from your last log file that you have network manager installed. For Network manager to work properly you need to have all network adapters disabled in System/Administration/Networking.

---

