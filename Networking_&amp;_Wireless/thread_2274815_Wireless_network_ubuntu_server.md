---
title: "Wireless network ubuntu server"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by Trandre on 2015-04-22
Hi I have installed Ubuntu server 14.10 and I want to connect to the router wirelessly with the Jensen AL25150 usb wireless card.

I am in the CLI interface trying to link wirelessly to the router. 

**My question is: How should I continue to troubleshoot?**

What have I tried?

**I am able to with success:** 
**1.** List the wireless accesspoint via the iwlist scan, and have Identified my router
**2.** Set essid via sudo iwconfig wlan0 essid nameofAccessPoint
**3.** Set the password through sudo iwconfig wlan0 key s:XXXXXXXX
So far this show correct Essid and a hex passphrase, but the accesspiont is not-assoiciated and nwid:Managed
- After reading on man iwconfig I try to alter the nwid to another state but this gives me an error for the nwid

**4.** I am able to set sudo ifconfig wlan0 up
when I try to enter sudo dhclient wlan0 it works for a long time and errors and it erases my iwconfig wlan0 settings.

[ATTACH]261476[/ATTACH]


```
Codename:    utopic



########## wireless info START ##########


Report from: 22 Apr 2015 21:05 CEST +0200


Booted last: 22 Apr 2015 16:56 CEST +0200


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
##### kernel ############################


Linux 3.16.0-34-generic #47-Ubuntu SMP Fri Apr 10 18:03:41 UTC 2015 i686 athlon i686 GNU/Linux


Parameters: ro


##### desktop ###########################


sed: can't read /home/tor-andre/.dmrc: No such file or directory
Could not be determined.


##### lspci #############################




00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
    Subsystem: ASUSTeK Computer Inc. Device [1043:80ff]
    Kernel driver in use: via-rhine


##### lsusb #############################


Bus 001 Device 006: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


/home/wireless_script.sh: 178: /home/wireless_script.sh: rfkill: not found


##### lsmod #############################


rt2800usb              26669  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              87254  1 rt2800usb
rt2x00lib              48794  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              567068  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              430618  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib


##### interfaces ########################




auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr 00:0e:a6:30:7b:23  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 34:21:09:09:20:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Telenor3336gry"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6368-6762-656F-6875-617A-716A-6F
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################




##### NetworkManager info ###############


/home/wireless_script.sh: 203: /home/wireless_script.sh: nmcli: not found


/home/wireless_script.sh: 205: /home/wireless_script.sh: nmcli: not found


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


/home/wireless_script.sh: 226: /home/wireless_script.sh: Syntax error: redirection unexpected



```

---

### Post by Trandre on 2015-04-22
Cleaned up post and replies, couldn't delete

---

### Post by Trandre on 2015-04-23
Clean up and consolidated post

---

### Post by Trandre on 2015-05-03
*bump*

---

### Post by Trandre on 2015-05-05
Bumpetibump

---

### Post by chili555 on 2015-05-05
The usual way to set up networking in a server is in the file /etc/network/interfaces. Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by Trandre on 2015-05-05
Hi and THX Chilli and Oldfred who has helped out on this query. I solved it by carrying the old machine up to the router and performed a series of updates and upgrades. and Presto now it connects. 

I think the solution was that the WIFI driver was not in the out of the box cd and I had to connect by hardwire to let the machine update it self. 

Now I am going to crack on getting a static IP as the post from Chilli will help me with.

---

