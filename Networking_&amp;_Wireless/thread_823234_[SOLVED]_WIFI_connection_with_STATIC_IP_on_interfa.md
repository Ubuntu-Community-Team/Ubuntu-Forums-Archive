---
title: "[SOLVED] WIFI connection with STATIC IP on interface(Proffessionals help please)"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ar_hnazari on 2008-06-09
Here is the exact concept of the problem:
I have a PC having a wired interface which is connected to internet by an ADSL modem configured to obtain IP address from a DHCP server, and 8.04 hardy is installed and properly configured and is using the internet without problem, the second interface is a D-Link WIFI card with Atheors chip and is working fine. DHCP3 is installed and configured on my PC and configured to assign addresses in 192.168.1.0 range with router option 192.168.1.10. A LinkSYS access point is configured as 802.11g with WPA-Personal security and IP address 192.168.1.254 and is working fine with no problem. Second computer is a HP Pavilion dv2725en 8.04 hardy installed and having an Intel PRO/Wireless 3945bg and connects to AP fine and no problem.
NOW WHAT'S THE PROBLEM????
I have to connect my PC's wifi card to access point using STATIC IP ADDRESS 192.168.1.10 so it can assign IPs to others through AP and act as NAT incoming interface, note that NAT is properly configured on my PC and is serving fine (tested another way :lolflag:).
I have configured my wifi interface on PC different ways:
First I used System->Administration->Network applet and configured my ath0 interface having a static IP, but it didn't connect!!!
Second using iwconfig,ifconfig,etc. commands and configured my wifi... no use!!!
Third using WIFI-Radar and doing so did no help!!!
Now is there anyone here who can help me solve my problem???
I comment that my PC scans the AP and can connect to it when configured in roaming mode but it is useless to me without the IP i described above :( .

---

### Post by ar_hnazari on 2008-06-09
wieman01 IS THE GREATEST...
I found [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) and tested it.
You may want to try it, if so feel LUCKY from now on...
Go ahead ... THANX MAN... YOU ARE PERFECT:guitar:

---

