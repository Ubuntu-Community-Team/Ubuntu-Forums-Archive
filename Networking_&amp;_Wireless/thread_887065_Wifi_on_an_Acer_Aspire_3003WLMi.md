---
title: "Wifi on an Acer Aspire 3003WLMi"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by tomwigwam on 2008-08-11
I've just installed Hardy on my brother's Acer Aspire 3003WLMi and can't persuade the wifi to work. looking around the forum, I see various explanations for activating the wifi card - if I put in "lspci | grep Broadcom\ Corporation" in the command line I get "00b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller". What do I need to do to install the drivers/firmware? At present I haven't tried connecting to the internet with a wired LAN, although it'll probably work.
This is my first Ubuntu install
Thanks
Tom

---

### Post by chili555 on 2008-08-11
Hook it up to an ethernet connection and once you get connected, open a terminal and do:```
sudo apt-get install b43-fwcutter
```It will download and install the firmware for you. After you detach the ethernet, you should be able to configure your wireless and connect.

---

### Post by tomwigwam on 2008-08-12
I've done that, and the wifi light is now on, but I'm not sure how to configure the connection - settings > administration > network doesn't seem to do the job. What do I need to do?

---

### Post by chili555 on 2008-08-12
> settings > administration > network doesn't seem to do the jobWhen you select the Properties of your wireless card, enter the ESSID, any encryption details, WEP, WPA, et al, and select DHCP, does it try and fail to connect, or what? What are your symptoms?

---

### Post by tomwigwam on 2008-08-12
Noe of the network manager tools seem to work - system > Preferences >Wireless network, and KWifiManager can't find any wireless networks - the light is on, but nobody's home(!). I'm not sure of the steps I need to take to make it go. Thanks

---

### Post by tomwigwam on 2008-08-12
It doesn't even seem to attempt to connect - the network is unsecured, what should I select as an option for the encryption?

---

### Post by chili555 on 2008-08-12
What is the interface that shows up in a terminal:```
iwconfig
```Guessing it's *wlan0*, please do:```
sudo iwlist wlan0 scan
```Do you get a result? Do you see your router's ESSID? Using an example of *linksys*, please try:```
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```Substitute your interface and ESSID here. Do you connect?

---

### Post by tomwigwam on 2008-08-13
If I do that, this is what happens:

sam@sam-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sam@sam-laptop:~$ sudo iwlist wlan0 scan

wlan0     Scan completed :

          Cell 01 - Address: 00:30:F1:FF:14:ED

                    ESSID:"belkin54g"

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz (Channel 11)

                    Quality=36/100  Signal level=-73 dBm  Noise level=-66 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:tsf=000000b6688c3816

          Cell 02 - Address: 00:1C:DF:3B:43:47

                    ESSID:"CrawfordNet"

                    Mode:Master

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=35/100  Signal level=-74 dBm  Noise level=-66 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:tsf=00000108954bcf03



sam@sam-laptop:~$ sudo iwconfig wlan0 essid belkin54g

sam@sam-laptop:~$ sudo dhclient wlan0

There is already a pid file /var/run/dhclient.pid with pid 5777

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wmaster0: unknown hardware address type 801

wmaster0: unknown hardware address type 801

Listening on LPF/wlan0/00:14:a4:5a:0b:10

Sending on   LPF/wlan0/00:14:a4:5a:0b:10

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

sam@sam-laptop:~$ 

Wireless does not connect, by the looks of it

---

### Post by chili555 on 2008-08-13
> Wireless does not connect, by the looks of it Correct. Let's try to encourage it a bit more:```
sudo iwconfig wlan0 essid belikin54g
sudo iwconfig wlan0 ap 00:30:F1:FF:14:ED
sudo dhclient wlan0
```This part:> Quality=36/100is a bit worrisome, but I'd think we should still connect, perhaps at a lower speed.

---

