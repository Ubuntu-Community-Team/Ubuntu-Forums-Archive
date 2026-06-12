---
title: "Running Term Server Clients &amp; Windows at same time"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by hsweet on 2007-05-25
I have been running a pilot Edubuntu lab in an old windows lab this year.  I have an A/B ethernet switch that routes all the client machines either to the LTSP server or the regular school DHCP server to run windows.  Works fine. But only one system works fully at a time.

I was wondering if it would be possible to eliminate the switch so we could run Windows and Linux at the same time.  I figure that win. machines would have to use the LTSP DHCP, get an IP and gateway address and connect to the rest of the network by gatewaying thru the LTSP machine like they do in Linux.

The LTSP clients are on 192.168.0.x while the school's dchp network number is 172.16.x.x.

---

### Post by Azzuron on 2007-08-30
if your school has a windows server with DHCP on it, you can setup the bootp options on that server for specific mac addresses. you need to make a reservation in the dhcp server for the client you want to network boot, then add the following options:

17, 66, and 67. You should be able to do that from one of the tabs in the dhcp server in windows. with these options enabled you will need to put in the server IP that is handing out the files, and then the tftp path info that you have in your dhcp3.conf file. its really quite easy, and i know someone has a howto on the forums about it, thats how i got that to work. 

  --Dave

---

