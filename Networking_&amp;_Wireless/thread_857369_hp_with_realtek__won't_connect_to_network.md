---
title: "hp with realtek  won't connect to network"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by fishhuntercraig on 2008-07-12
was told to be more specific in title - hope this is better :-)

i just installed 8.04 and cannot get my hp dv4000 with rtl-8139/8139C/8139C+ to connect to my neighbors wireless network

previous thread asked me to run these 2 commands

------------

from lspci

lo no wireless extensions
eth0 no wireless extensions
eth1 radio off ESSID:""
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate 0 kb/s Tx-Power=off Sensitivity=8/0
Retry Limit:7 RTS thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

and from lsusb

eth1 No scan results

--------------

so from here i have no clue - should i be inputting dns info and the like in the network admin - should i get a new wireless card - ????

any and all help or guidance is appreciated

craig

---

### Post by fishhuntercraig on 2008-07-14
still no love on the connect to network front

the router that i'm trying to connect to is an actiontec gt701wg from quest

after reading through the archives i find that there are too many options for us computer buyers as it appears that nearly every system is slightly different 

i did find 1 party who had the same issue and same dv4000 that had the same lspci info as mine - but the thread had no solution - and since i'm a newby i don't have enough posts in to contact the individual to see what he did to get his system working

from the archive polls it seems that i have a 50/50 chance that an hp system will attach to a wireless network without issue 

so i truly wonder if it would be easier to get a new wireless card 

thanks -any and all help is appreciated

craig

---

### Post by adldesigner on 2008-07-14
Try the following commands:

(Lists your hardware and extracts Network entries)
```
sudo lshw -C -network
```
(Lists any wireless network available in your area)
```
iwlist scan
```

Post the output of each one of those commands enclosed by CODE tags (for better code readability).
This should help us start to diagnose your issue.

---

### Post by fishhuntercraig on 2008-07-14
please excuse my ignorance - but don't know what code tags mean

however since this system i'm trying to get working is not online i'm typing exactly what i see on that coputer to this one - which is an xp machine that connects to the same wireless network without issue - perplexing to me

so here are my results

when i run the 1st command "sudo lshw -C network" i get

----------

PCI (sysfs)

---------

when i run the second command " iwlist scan" i get

----------

lo     interface doesn't support scanning

eth0    interface doesn't support scanning

eth1    no scan results

----------

thanks a bunch for wading - and weighing - in on this

craig

---

### Post by fishhuntercraig on 2008-07-15
hey folks - still trying to get my system to attach to the network - obviously without success

would this whole exercise be easier if i got a new wireless card

and if that is the case is there a card that is recommended

i really want to break free from microsoft :)

thanks for any direction

craig

---

### Post by adldesigner on 2008-08-02
Are you still having issues, mate?

---

