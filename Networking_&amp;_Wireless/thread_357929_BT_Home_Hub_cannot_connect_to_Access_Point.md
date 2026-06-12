---
title: "BT Home Hub cannot connect to Access Point"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by helliewm on 2007-02-10
I had to do a fresh install of 6.10 as my previous install was corrupt . Now I cannot connect to the Access Point. In Kwireless Assistant it is not even picking my essid BTHomeHub-D130.

I ordered a Netagar Modem/Router as suggested by BigKen but I still would like to get to the bottom of this. See outputs below which include ifconfig and iwconfig.


helen@helen-laptop:~$ sudo iwconfig ath0 essid BTHomeHub-D130 channel 1 
Password:
helen@helen-laptop:~$ sudodhclient ath0
bash: sudodhclient: command not found
helen@helen-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:12:17:78:e0:2f
Sending on   LPF/ath0/00:12:17:78:e0:2f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
helen@helen-laptop:~$ 

helen@helen-laptop:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:12:17:78:E0:2F  
          inet6 addr: fe80::212:17ff:fe78:e02f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0D:5E:3C:48:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-12-17-78-E0-2F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4160 errors:0 dropped:0 overruns:0 frame:70
          TX packets:548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:356722 (348.3 KiB)  TX bytes:29044 (28.3 KiB)
          Interrupt:10 Memory:f8b60000-f8b70000 

helen@helen-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11Ta  ESSID:"BTHomeHub-D130"  
          Mode:Managed  Frequency:5.21 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:3958  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

helen@helen-laptop:~$ 

IPv6 is enabled. Any suggestions??

Helen

---

### Post by spd106 on 2007-02-10
Hi, could you try this command ```
sudo iwlist ath0 scan
``` It should produce a list of APs in your local area. Try to identify which one you want to connect to. It may be advisable to change the ssid of your network to something less generic.

---

### Post by helliewm on 2007-02-10
Changed my essid to bamboo see screenshot below but the iwlist ath0 scan you suggested is not picking it up. See below:

helen@helen-laptop:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:7F:5A:4F:AD
                    ESSID:"BTHomeHub"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:0F:3D:96:F7:6E
                    ESSID:"G604T_WIRELESS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

helen@helen-laptop:~$ 

 
The other BTHomeHub listed is a neighbours, its definitely not mine. See screenshot where I have changed my essid . I am really stuck here???

Helen

---

### Post by spd106 on 2007-02-10
This is very strange, is there any way that you can verify the wireless AP is working correctly. Do you own or can you borrow another wifi device? Maybe scan a couple more times just to be sure.

Do you have ssid broadcast disabled? It should show up even without it, but still.

---

### Post by helliewm on 2007-02-10
No essid broadcast is enabled I have checked that.

BigKen from the forum runs his own computer business, he lives down the road from me ( I met him through the  forum) he has given a Network Card that works out of the box with Ubuntu so thats absolutely not a problem.

I did the other night get my very tempermental old Linksys Modem/Router working Wirelessly but thats not a solution. Its broken there is something wrong with power on that nothing to Ubuntu its the same in windows.

Ken told me to get a new Netgear modem/router I have bought a high speed 128 mpbs netgear from ebay for £30.00 just waiting for this to arrive.

I have scanned several more times but nothing. This Home Hub is new its bugging me I can't figure out what is wrong?

Helen

---

