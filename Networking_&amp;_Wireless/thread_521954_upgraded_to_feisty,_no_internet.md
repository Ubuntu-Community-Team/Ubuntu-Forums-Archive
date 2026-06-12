---
title: "upgraded to feisty, no internet"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by verthandi on 2007-08-09
hello good sirs and madames!

Started this thread after searching around the forums for the answer for almost a week ~sigh, my head is spinning~

Anyway, we have a Pentium 4 computer that worked well with Ubuntu 6.10. It connected to the internet with no problems (it has built-in LAN) using our DSL connection. When 7.04 arrived, we installed it on the same computer. It was a success but when we tried to connect to the internet using the same DSL connection, we couldn't.

In devices-network tools our network device shows "loopback interface". The other two were "ethernet interface (eth0)" and "ethernet interface (eth0:avahi)". whichever one we chose made no difference, still no internet.

We have tried "sudo pppoeconf", didn't work  (timed out). the message shows: 
"sorry, i scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

also tried "sudo pon dsl-provider", didn't work.
also tried changing the ipv6 value to "true" in firefox, still didn't work.
tried using a separate LAN card, still no connection.

i am no expert in ubuntu so any help will be highly appreciated. thank you so much! :)

---

### Post by linuxwizard on 2007-08-10
Look over this hopefully will help.

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by verthandi on 2007-08-13
@linuxwizard

thanks for the tips but unfortunately, the pppoeconf command doesn't work.
will try checking if the pppoe package is installed

we are now in the process of reinstalling feisty on an identical PC, this time
it's connected to the DSL modem (maybe it'll configure by itself)

will post an update later, thanks :)

---

### Post by verthandi on 2007-08-13
update:

reinstallation done, still no internet
did the bug fix #82287 (edited the interfaces file and the nsswitch.conf file)
still no internet

changed ipv6 value to true, nothing

please help! :confused:

---

