---
title: "No wireless connectivity on Sony VAIO Intel Pro/Wireless 2200BG"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by rtw_travel on 2008-09-30
This is a fresh install of 8.04LTS on a Sony VAIO VGN FS970 on what was formerly an increasingly slow windows xp machine. 

Everything works except the wireless network... which worked for a few minutes and then stopped. Wireless networking was also the only thing that did not work properly during the installation. Yes, the wireless model is turned on. Yes, the network works with other wireless devices on the network.

Your help is appreciated. Please be specific because I am not a Linux Geek. 

Here is technical stuff for my setup that I have seen requested on other similar posts:

david@vaio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:FA:15:46   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-43 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:8

david@vaio:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:FA:15:46
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-46 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2016ms ago



david@vaio:~$ lspci
... pile of stuff and then...
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by rtw_travel on 2008-10-01
Did more googling and found this post:
[http://www.linuxquestions.org/questions/linux-hardware-18/wireless-wpa-480895/](http://www.linuxquestions.org/questions/linux-hardware-18/wireless-wpa-480895/)

I entered the following three commands from the post by igorc (see link), and wireless now works. 
# iwconfig - just to check up if the card is up and running
# ifconfig eth1 up
# dhclient eth1

Works now... but can someone explain what I did (and will I have to do it again?)

Thanks

---

### Post by rtw_travel on 2008-10-01
rebooted and back to my old problem. However, here is another clue below when running dhclient. Any ideas what is going on? 

FWIW, I am using two D-Link routers in my home network. A DI-604 is connected to the cable modem for internet. The LAN ip is 192.168.0.3. . DHCP is on in this router. The wireless router (192.168.0.1) is a WBR-1310, and DHCP is off. 





david@vaio:~$ sudo dhclient eth1
sudo: unable to resolve host vaio
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:6f:7f:16:39
Sending on   LPF/eth1/00:16:6f:7f:16:39
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.101 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.101 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 192.168.0.101
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.

--- 192.168.0.3 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

---

### Post by rtw_travel on 2008-10-01
bump...anyone, please

---

### Post by knattlhuber on 2008-10-01
So the "ifconfig eth1 up" command does not work anymore?

You would need to put these commands along with your encryption settings into /etc/network/interfaces so that it connects when the computer boots. There an excellent HOWTO on that: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Alternatively, you could try a program like [Wicd]("http://wicd.sourceforge.net/download.php") to manage your network connections.

---

### Post by rtw_travel on 2008-10-19
Thanks for the reply. 

For posterity, I found the answer here. 
[http://ph.ubuntuforums.com/showthread.php?p=5615397](http://ph.ubuntuforums.com/showthread.php?p=5615397)

I have no idea why the 2200 provides a 'flaky' wireless connection, but this linked thread seems to provide a solution

---

