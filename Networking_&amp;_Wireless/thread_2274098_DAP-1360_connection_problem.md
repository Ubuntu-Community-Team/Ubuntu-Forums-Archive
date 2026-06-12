---
title: "DAP-1360 connection problem"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by ewm on 2015-04-17
I have a DAP-1360 WAP connected to my Ethernet port as a bridge to my wireless router. I have just done a clean install of Ubuntu 14.04 with the latest updates and can now no longer connect to the WAP using the default ip 192.168.0.50 or dlinkap even after a factory reset. Connecting to the wireless router using a cable works fine. Connecting the DAP-1360 to my Windows laptop Ethernet port  allows me to connect using dlinkap.
I have read most of the posts looking for a solution with no success, I am sure I have a setting wrong somewhere but cannot put my finger on the problem.
I have pasted the output of wireless-info.txt here pastebin.ubuntu.com/10841138. These results are with the DAP=1360 connected to the PCs Ethernet port. 
Any help would be much appreciated.
Eric
Further investigation shows that the problem seems to be that the DAP-1360 default ip 192.168.0.50 is outside the ip address range set by the wifi router when network/interfaces set to dynamic.
Problem solved - set all ip addresses in the same range and connection successful.

---

