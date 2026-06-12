---
title: "Linksys WMP54G and Edgy almost need help."
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by acolic on 2006-12-23
Hi,

I almost have the linksys wmp54g working with Edgy. I just need a bit of help to make it all work together.

Edgy has recognized the card. If I go to networking I see a wlan0 and wmaster0. I have configured and enabled the wlan0 with the static ip and gateway required to connect to my wireless router. It starts ok. I have tried to ping the router but I get a network unreachable error.

If I use SWSscanner the scanner sees my router, but no connection is being made.

I must be missing something. The wireless card seems to be working and the router is working and is reachable from the desktop because I am connecting to the wireless network from a laptop in the same room.

Any help getting the two to communicate is appreciated.

Alex

---

### Post by djRobbieF on 2006-12-23
Did you input your SSID and WEP/WPA pass key?

---

### Post by acolic on 2006-12-23
Hi,

I inputted my SSID. I turned off WEP/WPA.

Still no luck.

---

### Post by djRobbieF on 2006-12-23
Do you have WEP or WPA on the router though?  If not, that's VERY bad security practice - be warned  ;)

But if it's ON on the router, you'll need to enter your pass key on your computer in order to connect.

---

### Post by acolic on 2006-12-23
Hi,

I usually have it on but to narrow things down I turned it off.

Once I get the computer and router working, I'll deal with turning it on.

Alex

---

### Post by djRobbieF on 2006-12-23
Because you haven't said really how savvy you are, and no details were given about when you set the IP address, I'd suggest switching to DHCP (I presume your router has a DHCP server) and seeing if it connects then.

It'd be good if you'd provide more details, because then perhaps we can get to the root of the problem.

---

### Post by acolic on 2006-12-23
Hi,

I set my static IP via the networking wizard. But to make sure I have covered everything I have reset everything to use dhcp. I checked and I can connect to my network via my laptop wirelessly via DHCP. 

I also changed by SSID to make sure the network was reachable. I used the KDE SWScanner application and it found my new SSID. The signal was strong. I changed my wireless settings in the Network Settings app to use my new SSID. When I enabled the device a pop up showed up indicating that the network device was being activated.

That is as far as I get. There is no connection to the network. I checked the routers log file and no attempt was made to connect to it.

In the network settings app where you configure the SSID their is a box for a password and a drop down for password type. Since I have disabled WEP I have left those blank. Is that correct?

Any suggestions?

Alex

---

### Post by acolic on 2006-12-24
Hi,

I thought it might help if I post the results of iwlist and iwconfig:

IWLIST

acolic@ubuntu-desktop:~$ sudo iwlist wlan0 scan
Password:
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:CE:7D:82
                    ESSID:"Polaris"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:off
                    Extra:tsf=0000000945c3a80b

acolic@ubuntu-desktop:~$ 

IWCONFIG

acolic@ubuntu-desktop:~$ sudo iwconfig wlan0 essid Polaris

lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Polaris"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
sit0      no wireless extensions.

I then stopped wmaster0 and wlan0 and restarted them.

acolic@ubuntu-desktop:~$ sudo ifdown wmaster0
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 4693
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
acolic@ubuntu-desktop:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4687
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:14:8c:17
Sending on   LPF/wlan0/00:18:39:14:8c:17
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
acolic@ubuntu-desktop:~$ sudo ifup wmaster0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
acolic@ubuntu-desktop:~$ 
colic@ubuntu-desktop:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Input/output error
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:14:8c:17
Sending on   LPF/wlan0/00:18:39:14:8c:17
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I hope this helps someone figure out what is going on with my system.

Thanks

Alex

---

### Post by acolic on 2006-12-25
Hi,

thanks everyone for all your suggestions.

I installed winXP on the box and the card is working. 

My days of hacking OS systems to make things work ended years ago. I need things to work out of the box. 

I wanted to stay with Ubuntu but I didn't have days to spend on getting the wireless card to work and then spending more days working on getting the video to work properly.

In one hour I had everything working well. The cost of WinXP was more then made up by not spending days on getting it to work.

Thanks again,

Alex

---

