---
title: "SYN Flood to Host"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by rax_m on 2007-07-10
Hi, 

I noticed that on my ADSL router I am getting the following type of entries occasionally:

2007.07.09 13:28:54 **SYN Flood to Host** 192.168.1.3, 35990->> 209.170.119.20, 80 (from PPPoE1 Outbound)

Should I be worried? Do I need to do anything to stop this?

I don't have any ports open (default Feisty install) and my router is configured not to let anyone in (i think). 

Any advise would be appreciated ? 

Thanks :)

---

### Post by rax_m on 2007-07-11
anyone?

---

### Post by Synflux on 2007-07-12
Hi,

I could be wrong but from the looks of that line it's warning you about a high number of outgoing connections rather than incoming. This is probably to alert you in case your connection is being used to perform a DOS attack on some server.

It seems to be saying 'you are sending a high number of SYN (tcp sync) messages to port 80 (http) of this other computer' .  

This seems legitimate to me so I wouldn't worry about it.

---

### Post by rax_m on 2007-07-12
Hi Synflux .. thanks for the reply.. 
Not sure why that would be happenning? I'll keep an eye out. 
Maybe I should do a chrookkit (?) install/check or something. 
It is a fairly new install of feisty.. with the the universe repos install enabled an the only external is the ubuntu compiz fusion repos enabled. 

Rax

---

### Post by rax_m on 2007-07-22
Hi 

As I've still been feeling paranoid about security recently (especially since seeing recurrent occurrences of the above), I decided to to a chkrootkit

To summarise the output, a couple of things seemed to come up:

```

...
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/.systemPrefs
/lib/modules/2.6.20-16-generic/volatile/.mounted
...
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
...
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0:avahi: PACKET SNIFFER(/sbin/dhclient3[5717], /usr/sbin/avahi-autoipd[5712])
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[6046], /sbin/dhclient3[6096])
...

```

Can anybody give me advise on whether this is normal or not?

Thanks
Rax

---

