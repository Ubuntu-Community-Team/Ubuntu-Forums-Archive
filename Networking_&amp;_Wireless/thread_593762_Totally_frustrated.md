---
title: "Totally frustrated"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by d_thrasher on 2007-10-27
I have been working on getting wireless working since Fiesty.  Now I have Gutsy and even went so far as buying a new wireless card yesterday that was billed as "just works" (Trendnet TEW-443PI) and I still can't figure it out.  Please help.  Info below:

devo@devo-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:18:E7:2E:60:50  
          inet6 addr: fe80::218:e7ff:fe2e:6050/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:14:85:14:9F:FC  
          inet addr:192.168.1.38  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe14:9ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1507799 (1.4 MB)  TX bytes:263619 (257.4 KB)
          Interrupt:20 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-2E-60-50-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3781 errors:0 dropped:0 overruns:0 frame:2922
          TX packets:217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:321337 (313.8 KB)  TX bytes:9982 (9.7 KB)
          Interrupt:21 

devo@devo-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:E0:98:CC:54:D7
                    ESSID:"ThrasherNet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:18:39:3F:17:5F
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=192/70  Signal level=-159 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:09:5B:ED:5D:B2
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010006ff7f

devo@devo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
devo@devo-desktop:~$

---

### Post by JeremyLong on 2007-10-27
Install NetworkManager

sudo apt-get install network-manager-gnome

---

### Post by d_thrasher on 2007-10-27
OK, done.  Now what?

---

### Post by Lambert on 2007-10-27
> **d_thrasher said:**
> OK, done.  Now what?

If you open up network manager, you should be able to configure and connect to your wireless router.

network manager is still a buggy application.


To test connection from command line try tunning these commands in the terminal.

```

sudo iwconfig ath0 essid ThrasherNet

sudo dhclient ath0

```

you should now be connected with all network settings. If not more troubleshooting is needed. 

because you have an interface and can scan for access points, I don't think it's in the driver.

---

### Post by d_thrasher on 2007-10-27
It still isn't working...

---

### Post by Lambert on 2007-10-27
> **d_thrasher said:**
> It still isn't working...

So what happened after running those commands and what was the output?

After running iwconfig ath0 essid command then just run this command and post output here.

```

sudo iwconfig

```

After you ran the dhclient command did you get something that said nodhcpoffer or something else?

What type of encrytion are you using?

---

### Post by d_thrasher on 2007-10-27
Thanks for sticking with me, Lambert, I used to think I was pretty tech savvy, but this wireless stuff has me beat.

The commands you gave me breaks my wired connection.  All I could do to get it back is reboot.

Th output:

devo@devo-desktop:~$ sudo iwconfig ath0 essid ThrasherNet 
[sudo] password for devo: 
devo@devo-desktop:~$ sudo dhclient ath0 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wifi0: unknown hardware address type 801 
wifi0: unknown hardware address type 801 
Listening on LPF/ath0/00:18:e7:2e:60:50 
Sending on   LPF/ath0/00:18:e7:2e:60:50 
Sending on   Socket/fallback 
DHCPREQUEST on ath0 to 255.255.255.255 port 67 
DHCPREQUEST on ath0 to 255.255.255.255 port 67 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8 
No DHCPOFFERS received. 
Trying recorded lease 192.168.1.100 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. 

--- 192.168.1.1 ping statistics --- 
1 packets transmitted, 1 received, 0% packet loss, time 0ms 
rtt min/avg/max/mdev = 0.532/0.532/0.532/0.000 ms 
bound: renewal in 28029 seconds. 
devo@devo-desktop:~$ sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wifi0     no wireless extensions. 

ath0      IEEE 802.11g  ESSID:"ThrasherNet"  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off 
          Encryption key:526D-2C6B-426A-4264-6F3F-3820-58   Security mode:restricted 
          Power Management:off 
          Link Quality=33/70  Signal level=-59 dBm  Noise level=-92 dBm 
          Rx invalid nwid:1031  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

devo@devo-desktop:~$

---

### Post by d_thrasher on 2007-10-27
...and I'm using WEP.  My router doesn't seem to support WPA. I reset the WEP password on my laptop and the router to make sure it was working. I also rebooted my desktop - the machine with the issue into XP for the first time in ages to make sure it wasn't the card.  It works like a champ in XP.

---

### Post by Lambert on 2007-10-27
Try this. Run these commands

```

sudo iwconfig ath0 key restricted
sudo iwpriv ath0 authmode 2

sudo iwconfig ath0 essid ThrasherNet

sudo dhclient ath0

```

Post any errors or other information you think pertinent if this doesn't help.

---

### Post by d_thrasher on 2007-10-27
That last command just broke the connection again.

Could it be that I have both wifi0 and ath0?

I believe that the one report is showing that the hardware ID is wifi0 but it looks like the software is activating ath0.

Or does that make no sense at all?

---

### Post by d_thrasher on 2007-10-27
This didn't work either: [http://www.linuxforums.org/forum/linux-networking/59637-madwifi-connected-ap-but-cant-get-ip.html](http://www.linuxforums.org/forum/linux-networking/59637-madwifi-connected-ap-but-cant-get-ip.html)

---

### Post by d_thrasher on 2007-10-27
<bump>

---

### Post by Lambert on 2007-10-27
my last post forgot a piece. The command should be

sudo iwconfig ath0 essid ThrasherNet key _____

enter your wep key in the blank. the do the dhclient command.

---

### Post by d_thrasher on 2007-10-27
Sadly, there was no change.

Why would I be able to see the network, but not get any connection?  

Frustrating...

Are you sure it doesn't have something to do with the wifi0: unknown hardware address type 801 error?

---

### Post by d_thrasher on 2007-10-28
Does anyone have another suggestion?

---

