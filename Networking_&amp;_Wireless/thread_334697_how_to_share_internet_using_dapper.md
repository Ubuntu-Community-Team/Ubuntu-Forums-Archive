---
title: "how to share internet using dapper"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Linux Lover on 2007-01-09
i am using dapper in two machines which are connected with a crossover cable. one of these mahchines have two NIC, out of which one is connected to internet via DSL (dynamic ip). the other machine have one NIC and is connected with the other machine with that corssover cable.

i can ping to both of my machines from the other machine. Now i want to share the internet connection.

please guide me how to share the internet connection.

---

### Post by n3gbz on 2007-01-12
My set-up is similiar,

internet ---> wlan0 ---> Ubuntu Edgy ---> eth0 ---> PC

The internet is accessed via WiFi on a pc running Ubuntu Edgy.

I then use a crossover cable from eth0 to a second PC.

To get Internet Connection Sharing (ICS) to work, I needed to install firestarter and set a preference to allow Internet Connection Sharing.

The online firestarter documentation was a big help 
-- [http://www.fs-security.com/docs/](http://www.fs-security.com/docs/) -- 
especially the section on ICS 
-- [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php) --

The Ubuntu Edgy wiki 
-- [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) --
explained how to install firestarter 
-- [http://ubuntuguide.org/wiki/Ubuntu_E...restarter](http://ubuntuguide.org/wiki/Ubuntu_E...restarter) .29 -- a lot of good info there!!!

I hope this helps!!!

---

### Post by Linux Lover on 2007-01-13
Thank you for your post. I am also presently working using firestarter. i think it is the easiest way to share the internet connection. also shorewall is a good bet, but nothing to hide, i could not understand the shorewall steps. that is not for a blind like me. anyway, my internet sharing is up and running. though i have shifted a bit in distribution. i am presently using FC6 in server and FC5 in my client machine. Still, i am thinking back to ubuntu.... and surely be back using FC for a few days.

---

