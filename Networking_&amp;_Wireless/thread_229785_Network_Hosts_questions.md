---
title: "Network Hosts questions"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by Nrvnqsr on 2006-08-04
Hi,

I have a Wired/Wireless home network router using a Belkin F5D7230-4 in 
which:

1 PC is pure Dapper
1 PC is Dual Booting Dapper w/ WinXP
1 PC is pure WinXP

checking the router settings gives me a (null) for Dapper in the Host name section, the other 2 which are Windows PC are recognized.
this can be a problem when I'm planning to convert my mother's WinXP to Dual Boot and all 3 are running Dapper at the same time.

and the question is. Is this just a router issue? or it can be changed while in Dapper?

Apreciated (sp?)

---

### Post by spd106 on 2006-08-05
Yeah, this can be sorted by telling dhclient to send the hostname when it aquires an ip address.
In the /etc/dhcp3/dhclient.conf file, add this line somewhere
```
send host-name "DapperLTS";
```
Swapping DapperLTS for your hostname. This works on my belkin router, though I had to install winbind to allow hostname resolutions through ping etc.Samba works ok without it.

---

### Post by Nrvnqsr on 2006-08-05
Thank you very much for the response it worked perfectly with my router, and it also give me an evil scheme some how :KS

---

