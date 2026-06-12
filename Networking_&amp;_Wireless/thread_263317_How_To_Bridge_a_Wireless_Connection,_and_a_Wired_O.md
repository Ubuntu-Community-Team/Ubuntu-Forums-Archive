---
title: "How To Bridge a Wireless Connection, and a Wired One"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by mrphantastic on 2006-09-23
I built my own computer, and I am running Ubuntu 6.06 LTS with a Linksys Wireless PCI-Adapter (WMP54G).  All I want to do is connect my Xbox 360 to the computer (which I have already succesfully done w/WinXP), via wireless connection, then bridge that with the wired connection to my college's intranet.  I am already sure that I have connectivity to the college (Wired connection w/just the computer, that is).  I want to do an ad-hoc type network between the PC + the Xbox 360 (i.e. I have no wireless access point, just a wired connection to the college intranet).  The problem maybe that the college uses a Cisco Clean Access Agent Network program, and Symantec Antivirus (commercial grade).  I am not sure what on earth I should do.....   Any suggestions?????

---

### Post by steve-tm on 2006-09-23
Sorry about spelling I am dislex

First point of intrest is you can setup your pc to be an AP by ishing the command "sudo iwconfig xxx mode master"  where xxx is the name of your wifi card in my case that "ath0".  From this point on you pc is an AP

Second I don't know about briging but perhaps looking at my setup may help

One PC conected to the internet, one laptop wired though ethernet and one laptop conected wifi  all 3 computers can see each other even if I run XP on a laptop.

The PC uses ppp0 on a dynamic address set by my ISP

It also runs "NAT" sutup by "GUIDEDOG"  (this alows other computers on the network to access the network) on WINDOWS it's caled "internet sharing"

The PC has ethernet card set to eth0 - 192.168.0.2
and WIFI card set to ath0 - 10.0.0.2

I also run "bind9" in it's basic for have not setup any domains/zones

A dhcpd server set to lisen to eth0 and ath0
nameserver set to 192.168.0.2
and a pool of addresses eth0 192.168.0.10 - 192.168.0.20
netmask 255.255.255.0
and gateway 192.168.0.2

or ath0 10.0.0.10 - 10.0.0.20
netmask 255.0.0.0
and gateway 10.0.0.2

each meachin that conects to iver the ethernet or wifi gets one of the above addresses and gatways

or you can setup statict address outside of the pool ranges and it will work aslon as the flowing rauls are applied

address must start 192.168.0.n    or  10.0.0.n
with gatway 192.168.0.2  or 10.0.0.2
and names server iver 192.168.0.2 or 10.0.0.2

with this setup I can share the internet

include samba, nfs and cupsys files and printers.

include saned share one scanner

include imap, fetchmail and sendmail (for me sendmail works out the box where as postfix dousnot)  to have a central mail server so that each user can see the same mail from any mechin

I am shour that this is not the best setup but it works for me.

---

