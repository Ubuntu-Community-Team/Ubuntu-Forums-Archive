---
title: "Almost Wireless"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by cdom on 2007-04-02
Folks, I'm willing to go through the learning curve with Linux, but this wireless thing has me baffled. (Dapper 6.06). Dlink DWL-g630 wireless card.
So far I've tried all the possible upgrades, ndiswrapper,madfifi, and installing the native win driver. Nothing has changed from the initial installation.So now I'm confused.

The card shows activity with its LED's.
It shows up in network manager as being active.
I CAN ping the laptop from my desktop,
  
The problems!!!!
No internet. Cannot ping the desktop. When I do a hardware scan with the Device Database (device manager) the laptop locks when it scans for networking.
When I launch Wireless Assistant it tells me that I need turn on the card with the computer's (Vio pcg-f540) radio switch. This is the most baffling since I cannot find references anywhere about the laptop's radio switch. Including Sony's support site.??????????

Will accept any suggestions.  Thank you!!!

---

### Post by jonroboue on 2007-04-02
I've played with a few different distros trying to get one that worked with my wireless flawlessly. You might want to try Sabayon. You might have to do some minor tweaks but for the most part it just works. If you are really wanting to learn Linux then I would stick with Ubuntu.

---

### Post by chili555 on 2007-04-02
May we please see the output when you open a terminal and type the following:```
iwconfig
```One of the interfaces will show a bunch of text; the others will show 'no wireless extensions.' The one you found may be wlan0 or eth1 or otherwise. That is your wireless interface. 

Also post back the results of:```
iwlist <your_wireless_interface> scan
```

We'll get it going.

---

### Post by cdom on 2007-04-02
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

 iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"belkin"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by chili555 on 2007-04-02
Sorry if I didn't make myself clear here. Let's see ```
iwlist ath0 scan
```

---

### Post by cdom on 2007-04-02
iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:11:50:1E:55:81
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

### Post by chili555 on 2007-04-02
See in your iwconfig it says the ESSID is belkin? In scan, it shows the router is belkin54g? These are incompatible. Please open a terminal and do:```
sudo iwconfig ath0 essid belkin54g
sudo iwconfig ap 00:11:50:1E:55:81
sudo dhclient ath0
```Let us know.

---

### Post by cdom on 2007-04-02
john@john-laptop:~$ sudo iwconfig ath0 essid belkin54g
john@john-laptop:~$
john@john-laptop:~$ sudo iwconfig ap 00:11:50:1E:55:81
Error : unrecognised wireless request "00:11:50:1E:55:81"
john@john-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:13:46:c4:5a:80
Sending on   LPF/ath0/00:13:46:c4:5a:80
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 971961772 seconds.
john@john-laptop:~$

Sorry, cannot continue at this time as I have to get to work.Will continue to monitor this thread. Thanks for the replies.

---

### Post by chili555 on 2007-04-02
Nothing left to monitor! You are connected!```
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 971961772 seconds.
```

Good luck and have fun!

PS - I goofed on one command. It should have been:```
sudo iwconfig **ath0** ap 00:11:50:1E:55:81
```

---

### Post by cdom on 2007-04-02
Mr. chili555 ----  I am connected. On to bigger and goof ups. Thank you!!!!!

---

