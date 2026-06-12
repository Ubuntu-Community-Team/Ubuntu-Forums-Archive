---
title: "Can somebody help me in reading the syslog"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by gchiacch on 2010-09-07
Hello,
 
my problem is the wireless connection at home using the WEP encryption. I open a thread few hours ago and got some answer that suggested me to change the security from WEP to WAP2. To do this I have to change my router and this should happen in the next 10 days, even if I have to comment that others that reported a problem like mine solved by some configuration CLI command. (as described in my previous thread "WEP encryption setting not working on Ubuntu 10.04").
 
While investigating I found something in the syslog that I would like to know more about. It seems that connection with my Home AP (ROS48 ) was established ... but then for some reason that I'm unable to understand it timeout... (I attached the relevant part of syslog). Hereafter some message that seems relevant to me
 
<Sep 7 19:37:23 IT015485 NetworkManager: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'ROS48'.>
<Sep 7 19:37:23 IT015485 NetworkManager: <info> dhclient started with pid 3386>
<Sep 7 19:37:55 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20>
<Sep 7 19:38:09 IT015485 NetworkManager: <info> (wlan0): DHCP transaction took too long, stopping it.>
<Sep 7 19:38:09 IT015485 NetworkManager: <info> Activation (wlan0/wireless): could not get IP configuration for connection 'Home'.>
 
Is somebody with a better knowledge than me able to figure out what was going wrong, or in case is there some other tool like a trace that could be activated to capture additional messages?
 
I'd like to find a fix if there is any before trying the suggested solution.
Thanks for your help

---

### Post by JohnHeikkila on 2010-09-07
Try connecting manually via console.

*sudo iwconfig wlan0*
to see your wlan status (replace wlan0 with your wlan device, default wlan0)
then *sudo iwconfig wlan0 essid (your network's essid/name)*
*sudo iwconfig wlan0 key (your WEP passphrase as [Hexadecimal]("http://www.string-functions.com/string-hex.aspx"))*
then after this, check *sudo iwconfig wlan0*. If the part saying "Access point" is something like "None", then do *sudo iwlist scan* and when your wlan device finds the wireless network, search for the "Access-point" of your network. Usually the access-point is something like this: "00:0C:C3:7B:E9:94"
After you get the AP, do *sudo iwconfig wlan0 ap (the access point string)*.
If after this *sudo iwconfig wlan0* is "reset" like the ESSID and Key is blank again, something is wrong, but if it gets the AP, do *sudo dhclient wlan0*.

---

### Post by gchiacch on 2010-09-07
[SIZE=2]to JohnHeikkila,[/SIZE]
[SIZE=2]as reported in my previuos thread I used those CLI commands and the [/SIZE][SIZE=2]iwconfig wlan0 shows the result reported in the attached file.[/SIZE]
[SIZE=2]Tomorrow I will repeat [/SIZE][SIZE=2]the sudo dhclient wlan0 checking the syslog and I post the related messages. Have you had a look at the syslog I previously attached? Anything wrong there?[/SIZE]
[SIZE=2]Thank you for your time.[/SIZE]

---

### Post by gchiacch on 2010-09-08
Hello JohnHeikkila
following are the messages logged to syslog when I issued 'sudo dhclient wlan0' command, I don't know what are the ip addresses listed at the end of messages for sure they are not within the range of my network which goes from 192.168.1.2 to 192.168.1.254. Any idea? Thanks again for your time.
 
Sep 8 08:11:44 IT015485 dhclient: Internet Systems Consortium DHCP Client V3.1.3 
Sep 8 08:11:44 IT015485 dhclient: Copyright 2004-2009 Internet Systems Consortium. 
Sep 8 08:11:44 IT015485 dhclient: All rights reserved. 
Sep 8 08:11:44 IT015485 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 
Sep 8 08:11:44 IT015485 dhclient: 
Sep 8 08:11:44 IT015485 dhclient: Listening on LPF/wlan0/00:27:10:28:de:84 
Sep 8 08:11:44 IT015485 dhclient: Sending on LPF/wlan0/00:27:10:28:de:84 
Sep 8 08:11:44 IT015485 dhclient: Sending on Socket/fallback 
Sep 8 08:11:48 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
Sep 8 08:11:51 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
Sep 8 08:11:57 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 
Sep 8 08:12:17 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
Sep 8 08:12:29 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 
Sep 8 08:12:45 IT015485 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
Sep 8 08:12:49 IT015485 dhclient: No DHCPOFFERS received. 
Sep 8 08:12:49 IT015485 dhclient: No working leases in persistent database - sleeping. 
Sep 8 08:12:49 IT015485 avahi-autoipd(wlan0)[2168]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110). 
Sep 8 08:12:49 IT015485 avahi-autoipd(wlan0)[2168]: Successfully called chroot(). 
Sep 8 08:12:49 IT015485 avahi-autoipd(wlan0)[2168]: Successfully dropped root privileges. 
Sep 8 08:12:49 IT015485 avahi-autoipd(wlan0)[2168]: Starting with address 169.254.7.204 
Sep 8 08:12:53 IT015485 avahi-autoipd(wlan0)[2168]: Callout BIND, address 169.254.7.204 on interface wlan0 
Sep 8 08:12:57 IT015485 avahi-autoipd(wlan0)[2168]: Successfully claimed IP address 169.254.7.204

---

### Post by CharlesA on 2010-09-08
It's not connecting to the wireless network. DHCP is timing out trying to find an IP address.

It automatically gives you a 169.254.x.y if it can't get an address from DHCP.

---

### Post by gchiacch on 2010-09-08
Thanks for the explanation at least I wont waste additional time in trying to figure out where those addresses are coming from.
 
> **CharlesA said:**
> It's not connecting to the wireless network. DHCP is timing out trying to find an IP address.
 
It automatically gives you a 169.254.x.y if it can't get an address from DHCP.

---

