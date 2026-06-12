---
title: "wakeonlan with multiple network ports - direction to desired port"
date: 2023-04-07
forum: Networking &amp; Wireless
---

### Post by JimLS on 2023-04-07
Have wakeonlan set up and was working until I added a second lan card to the sending PC.  It now fails to start the other PC - not sure if it always fails or randomly.  I am using the simple command in cron as a user:

/usr/bin/wakeonlan  01:02:03:04:05:06    (with the proper MAC of course and time options preceeding that!)

I just logged into the machine and sent it from the command line expecting it to fail but it worked.  So a little puzzled how to test any changes if it sometimes works.

I see there is an option to add and IP address.  Will something like

/usr/bin/wakeonlan -i 192.168.1.255 01:02:03:04:05:06

force the output to use the network port with that subnet?

---

### Post by JimLS on 2023-04-09
I didn't do extensive testing but 

/usr/bin/wakeonlan 01:02:03:04:05:06
seems to work although it is suspected that it may send to the wrong network sometimes.  That's what was in cron and wasn't working.

So I tried forcing it to the other network and this failed (as expected):
/usr/bin/wakeonlan -i 192.168.2.255 01:02:03:04:05:06

So I modified the cron entries to this (with proper leading stuff for scheduling):
/usr/bin/wakeonlan -i 192.168.1.255 01:02:03:04:05:06

---

