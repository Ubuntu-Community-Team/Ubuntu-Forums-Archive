---
title: "help with interent connection sharing"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Schinoble on 2007-10-09
Presently i have win xp on my main machine with internet through a network card and has a wifi card connected to it that i use to share internet to a ubuntu machine, I'm trying get rid of winXP all together but cant get ubuntu to create an internet connection sharing. any help would be much appreciated.

i've used

modprobe -r ath_pci
modprobe ath_pci autocreate=adhoc
iwconfig ath0 essid laptop channel 2 key s:12345 rate 11M
ifconfig ath0 192.168.0.1
ifconfig ath0 up

and

iwconfig ra1 mode ad-hoc essid laptop channel 2 key s:12345 rate 11M
ifconfig ra1 192.168.0.2
ifconfig ra1 up

Iwlist scan results - from laptop

Cell 01 - Address: 02:16:E3:24:78:8E
ESSID:"laptop"
Mode:Ad-Hoc
Frequency:2.417 GHz (Channel 2)
Quality=54/94 Signal level=-41 dBm Noise level=-95 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100


iwconfig results - from laptop

ath0 IEEE 802.11g ESSID:"laptop" Nickname:""
Mode:Ad-Hoc Frequency:2.417 GHz Cell: 02:16:E3:24:78:8E
Bit Rate=11 Mb/s Tx-Power:16 dBm Sensitivity=0/3
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=29/94 Signal level=-62 dBm Noise level=-91 dBm
Rx invalid nwid:11 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Any ideas why i cant ping one computer from the other ?

---

### Post by sonicx on 2007-10-09
if you have to local machines in the same subnet  without any fancy settings, a ping machine a to b should always work. if it doesnt - your network cards ips arent setup correctly or there is a wrong route setup or your firewall is blocking traffic.....lots of things could be the reason.
some questions to think about:
has ath0 a valid ip? (cant see one in your output)
if it doesnt do something like
ifconfig ath0 inet 192.168.0.X netmask 255.255.255.0
why using ad-hoc mode and not managed mode??
set your gateway (the machine connected to the inet) to accesspoint mode (master mode) and your clients to managed mode.
have you setup iptables to forward and masquerade your clients traffic? (ping from client to gateway should work first)

and by the way - when you post more output, mark which output comes from which machine (gateway/router or client?) in your network.
regards,
sonicx

---

### Post by Schinoble on 2007-10-10
Hi sorry for the scanty information, only just started using ubuntu/linux about a month now and still getting to grips with whats important or not, i did finally manage to get the internet shared across both computers and would really appreciate any help cleaning things up and also the laptop only seems to connect for a short time before loosing connection, than having to run dhclient ath0 to get a new lease to use the net again, this seems to happen every 5 minutes or so, this is how i'm connecting, 

on the main computer, using a wireless card ra1 and an ethernet card connected to the net as eth0 , off the laptop i'm using ath0 as the wifi card. 

Prior to running the script I installed firestarter and enabled internet connection sharing and DHCP for the local network, created a new DHCP configuration ranged 192.186.0.1 to 192.168.0.255, the name server i left <dynamic>.

on the main computer i'm running a .sh file that i put together through various guides from this and other forums which reads, 

sudo ifdown ra1
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient eth0
sudo iwconfig ra1 mode ad-hoc
sudo iwconfig ra1 channel 2 
sudo iwconfig ra1 essid laptop
sudo iwconfig ra1 key s:12345
sudo iwconfig ra1 rate 11M
sudo ifconfig ra1 up
sudo dhclient ra1
sudo ifconfig ra1 192.168.0.1 netmask 255.255.255.0

(i did try the iwconfig ra1 mode master, but it gave me an error message
    Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra1 ; Function not implemented.
)

when i sudo iwconfig i get 

ra1       RT61 Wireless  ESSID:"laptop"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 02:16:E3:24:78:8E   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:3135-3234-33
          Link Quality=90/100  Signal level:-48 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

when i sudo ip address i get

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0b:6a:05:54:30 brd ff:ff:ff:ff:ff:ff
    inet **.***.***.**/22 brd 255.255.255.255 scope global eth0
    inet6 fe80::20b:6aff:fe05:5430/64 scope link 
       valid_lft forever preferred_lft forever
3: ra1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:15:e9:af:2a:18 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.1/24 brd 192.168.0.255 scope global ra1
    inet6 fe80::215:e9ff:feaf:2a18/64 scope link 
       valid_lft forever preferred_lft forever

on the laptop i'm running a .sh file that reads 

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo ifconfig ath0 down
sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=adhoc
sudo iwconfig ath0 channel 2
sudo iwconfig ath0 key s:12345
sudo iwconfig ath0 essid laptop
sudo iwconfig ath0 rate 11M
sudo ifconfig ath0 192.168.0.3 netmask 255.255.255.0
sudo route add default gw 192.168.0.1
sudo ifconfig ath0 up
sudo dhclient ath0

sudo iwconfig gives off this

ath0      IEEE 802.11g  ESSID:"laptop"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 02:16:E3:24:78:8E   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/94  Signal level=-48 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ip address gives out this

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
4: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:a0:d1:3d:33:ae brd ff:ff:ff:ff:ff:ff
5: wifi0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 199
    link/ieee802.11 00:16:e3:24:78:8e brd ff:ff:ff:ff:ff:ff
6: ath0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc noqueue 
    link/ether 00:16:e3:24:78:8e brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.56/24 brd 192.168.0.255 scope global ath0
    inet6 fe80::216:e3ff:fe24:788e/64 scope link 
       valid_lft forever preferred_lft forever

sudo dhclient ath0 gives this

There is already a pid file /var/run/dhclient.pid with pid 5705
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:e3:24:78:8e
Sending on   LPF/ath0/00:16:e3:24:78:8e
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.56 -- renewal in 8461 seconds.


any help tidying this up and making the connection last longer would really be appreciated, any more information i can supply just let me know how to do it, outside the stuff above i don't really know anything else

---

