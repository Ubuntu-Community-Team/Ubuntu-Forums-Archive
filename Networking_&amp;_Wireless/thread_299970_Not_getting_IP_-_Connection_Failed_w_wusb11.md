---
title: "Not getting IP - Connection Failed w/ wusb11"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by digivore on 2006-11-15
Hi, i'm having a problem getting my wireless USB nic working.  It seems that the wusb11 can see the router, but when i try to connect to it, i only get a connection failed in the 'wireless assistant 0.5.5'

I had this card working in dapper, but have recently fresh installed edgy, now i can't get it running.   When i was in dapper, the only thing i had to do was make sure i typed in 'sudo iwconfig wlan0 essid any'.  If i didn't do this i would get a message saying 'the radio in your wireless card is turned off'  when i try to scan for my router.    so i would type that and then i'd be set to go.  

But now, I can see my router, and i click  on it to connect, and it says connecting, but i cannot get an IP.  it says 'conection failed'.  I have tried 2 routers.   

I have tried disabling IPV6, restarting. and other things.

here are some of my outputs...

```
digivore@digitalis:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:91:B9:6B
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe91:b96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1815248 (1.7 MiB)  TX bytes:154179 (150.5 KiB)
          Interrupt:10 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:57:70:99
          inet6 addr: fe80::20c:41ff:fe57:7099/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:347306 (339.1 KiB)  TX bytes:113577 (110.9 KiB)

digivore@digitalis:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"default"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:1D:AA:D4
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:off
          Power Management:off
          Link Quality=0/0  Signal level=65/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

digivore@digitalis:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:1D:AA:D4
                    ESSID:"default"
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Quality:0/0  Signal level:26/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s


digivore@digitalis:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:57:70:99
Sending on   LPF/wlan0/00:0c:41:57:70:99
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.107 -- renewal in 278265 seconds.
```


Maybe someone has some ideas?

really frustrated.

Thanks.

---

### Post by digivore on 2006-11-17
still stumped...   
i know it's a weird one..

---

### Post by FrodoB on 2006-11-17
> **digivore said:**
> Hi, i'm having a problem getting my wireless USB nic working.  It seems that the wusb11 can see the router, but when i try to connect to it, i only get a connection failed in the 'wireless assistant 0.5.5'

I had this card working in dapper, but have recently fresh installed edgy, now i can't get it running.   When i was in dapper, the only thing i had to do was make sure i typed in 'sudo iwconfig wlan0 essid any'.  If i didn't do this i would get a message saying 'the radio in your wireless card is turned off'  when i try to scan for my router.    so i would type that and then i'd be set to go.  

But now, I can see my router, and i click  on it to connect, and it says connecting, but i cannot get an IP.  it says 'conection failed'.  I have tried 2 routers.   

I have tried disabling IPV6, restarting. and other things.

here are some of my outputs...

```
digivore@digitalis:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:91:B9:6B
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe91:b96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1815248 (1.7 MiB)  TX bytes:154179 (150.5 KiB)
          Interrupt:10 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:57:70:99
          inet6 addr: fe80::20c:41ff:fe57:7099/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:347306 (339.1 KiB)  TX bytes:113577 (110.9 KiB)

digivore@digitalis:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"default"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:1D:AA:D4
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:off
          Power Management:off
          Link Quality=0/0  Signal level=65/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

digivore@digitalis:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:1D:AA:D4
                    ESSID:"default"
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Quality:0/0  Signal level:26/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s


digivore@digitalis:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:57:70:99
Sending on   LPF/wlan0/00:0c:41:57:70:99
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.107 -- renewal in 278265 seconds.
```
Maybe someone has some ideas?

really frustrated.

Thanks.

If I saw that the card were bound to an address like this I would open a terminal and try to ping something like google.com and see what I got.

DHCP says you are connected and you did get an address, thats good. 
iwconfig says your signal quality stinks, it may not be true, Are you using ndiswrapper or a native driver?

What is the version number of your WUSB11?

---

### Post by digivore on 2006-11-17
Using the native driver, kubuntu picked it up.

It's a wusb11 v.2.8.

just tried this  command:

```
digivore@digitalis:~$ sudo dhclient wlan0
Password:
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:57:70:99
Sending on   LPF/wlan0/00:0c:41:57:70:99
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
digivore@digitalis:~$ 
```

---

