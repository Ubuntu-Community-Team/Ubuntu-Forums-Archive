---
title: "[SOLVED] setting a Ubuntu 7.10/Dlink wireless network"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Bobrm2 on 2007-11-16
I have the following situation: Attempting to create a wireless network with two computers Linux (Ubuntu 7.10 and XPpro), an HP PSC 2400 all in one. Have a DLink WDA1320 ethernet card searching for the DLink WBR1310.

Prior to installing Ubuntu, I had no problems with a wireless network involving the same equipment, also the equipment is less than a month old i.e. new linux box/router/Ethernet card. I believe the printer to be a seperate issue. All equipment is connected to the back of the router or in the case of the printer to the USB ports.

Have confirmed that madwifi_tools is reinstalled and works very well with DLink ethernet cards, according to madwifi´s web site. Also, have downloaded the most recent madwifi files/drivers for the atheros chip set, have not figured how to ¨make¨ the install upgrade.

have the following info, I have little understanding as to it&#347; meaning(s):

bob@Bob:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MSHOME00"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:55:54:7F   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-46 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bob@Bob:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1C:F0:55:54:7F
                    ESSID:"MSHOME00"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-46 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

bob@Bob:~$ 


networks are set up with WEP security on the router (WBR1310), ten digit code confirmed.   Set to DCHP.

It is oblivious to me that I do not understand the problem, so can't ask the question. Would someone get me started back on the right track.  You help most appreciated.

Bob

---

### Post by Fire_Chief on 2007-11-16
Not sure what you are having trouble with. The information you posted indicates that you are connected to the router [assuming you configured the router with a network name (SSID) of **MSHOME00**]. Since you are running DHCP, do you get an IP address from your configured pool on the router (ifconfig)? Can you browse to the Internet? Can you ping the XP box from Ubuntu and vice versa? If you've answered yes to all of these questions then the wireless is working properly.

---

### Post by Bobrm2 on 2007-11-16
I disconnected the ethernet cables from the machine (Ubuntu) that also has the WDA 1320 ethernet card. and was unable to connect to the internet. Thanks for your response

---

### Post by Bobrm2 on 2007-11-21
I disconnected the ethernet cables, between the router and computer, unchecked the box marked wired connection in System > Administration Network Settings. All is fine:).

There are several aliases listed under Hosts; with Local Hosts 127.0.0.0 predominate. The lists of IP address/Aliases contains items I know nothing about; suppose the computer generated them, but why?

Thanks for you help.

Bob

---

### Post by Bobrm2 on 2007-12-08
This has been solved, with the exception to a wireless connection to the HP PSC 2410 all in one. Will use another post to continue searching. Thank you all.


Bob

---

