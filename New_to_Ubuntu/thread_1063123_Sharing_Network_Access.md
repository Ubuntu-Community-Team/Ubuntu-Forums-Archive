---
title: "Sharing Network Access"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by photonian on 2009-02-07
CDMA access and Sharing it with home network on Intrepid
I connect to the Internet using CDMA (Verizon Mobile Service)and want to share my internet connenction via eth0 (local home network).
Everytime I have an Internet connection through CDMA (ppp0) then plug the network cable in (eth0), the system (Ubuntu Intrepid) starts looking to eth0 for the Internet and ignores my ppp0 connection.
After this I no longer can get on the internet, because although ppp0 is still up the system will only look at eth0 for the Internet.

I can unplug the ethernet(eth0) then the system will turn back to my already online ppp0(CDMA) and give me access to the internet, but then of course I can't share my internet connection with my home network.

[CENTER]**I need to _share my CDMA (ppp0) internet connection_ with my Home Network (eth0)**[/CENTER]


Please HELP!

P.S.
In Hardy I Used:

   1. Network Manager for eth0
   2. gnome-ppp for ppp0
   3. And Firestarter for DHCP and Sharing from ppp0 to eth0


But this doesn't work in Intrepid, even when I got gnome-ppp to work for ppp0 (for which I had to make a group with ID 30 and include myself in the group)

[CENTER]:confused:](*,)](*,)](*,)](*,):cry:[/CENTER]

---

### Post by x22 on 2009-02-07
did you try "dhclient ppp0" to get an address?

---

### Post by photonian on 2009-02-07
"dhclient ppp0" Didn't work
And after This didn't work I unpluged the ethernet, but the system didn't automaticly revert back to ppp0 for the internet. I had to disconnect ppp0 and reconnect.

so anyway here's the output if that helps:
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

ppp0: unknown hardware address type 512
ppp0: unknown hardware address type 512
Listening on LPF/ppp0/
Sending on   LPF/ppp0/
Sending on   Socket/fallback
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ppp0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


**Still need Help**
[:-)]

---

