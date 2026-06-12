---
title: "How to change DNS Server Address. It keeps resetting after reboot"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by boast on 2007-10-27
I changed IP's of my local DNS server, but ubuntu still keeps using the old IP. I edited it in network settings, changed it in /etc/resolv.conf to no avail.

My gateway, running pfsense, has the correct DNS ip set, so it cannot be obtaining the dns IP from the NAT....

---

### Post by kevdog on 2007-10-27
In my signature there is a tutorial for connecting from the command line.  At the bottom of this tutorial this is a link for using OpenDNS.  This should help you (btw you dont have to use the opendns servers, however this will tell you all the places and what files need to be modified if you want to manually specify any dns server you want to use)!!

---

### Post by archon256 on 2008-02-01
I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

---

