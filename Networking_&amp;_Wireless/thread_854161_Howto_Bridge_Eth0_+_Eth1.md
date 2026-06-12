---
title: "Howto: Bridge? Eth0 + Eth1"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by sanike on 2008-07-09
I'm not sure if Bridging is what I'm looking after...

When I was using windows, I had eth0 running to my DSL (dynamic IP, assigned by ISP), and eth1 to my Laptop which took the DSL connection from the PC, through my PC through a bridge...

Yet some people are saying (after searching) that routing is what I want not bridging, I already did the following

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1


I didn't set any IPs except for Eth1 as 192.168.0.1, but I noticed that my DSL was off at this point and pon dsl-provider did nothing, as soon as I removed the bridge it worked fine again.

Also this is to a Windows XP machine, so I need to enable another protocol to do this don't I?

Thanks in advance

---

### Post by kevdog on 2008-07-09
It sounds like you want to share your internet connection.  This is most likely under the topic of ICS or Internet Connection Sharing.  Internet Connection Sharing works through routing (layer 3).  You could also accomplish this through the use of Network Bridging (layer 2), however given your scenario, ICS should be a more efficient solution in terms of packet routing and preventing a lot of packets being bounced back and forth between the two computers.  There are a few ICS tutorials -- for beginners such as yourself -- I would look for tutorials that address this situation by using Firestarter to set up the internet connection sharing.  This is the easiest solution, however not the only solution available.

---

### Post by sanike on 2008-07-09
Thanks for the ICS tutorial, I'll research and attempt it

I just want whatever will be the most efficient :)

---

### Post by Trollslayer on 2008-07-09
Install 'Firestarter' through the Synaptic package manager - this gives you a firewall and has a wizard that sets up your internet ocnnection sharing as well.

---

### Post by sanike on 2008-07-11
Maybe I'm dumb but I can't seem to get ICS working within Firestarter...

I have it installed and set up as per the helpfile...

but as soon as it connects on my laptop and the firewall goes on I cannot get any traffic through on my laptop nor will Pidgin work anymore :)

probably ebcause I have to allow pidgin, but I did allow all connections from the laptop's IP

---

### Post by sanike on 2008-07-12
I checked out an older version of an ICS document

[http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

and it seems to have confused me more, can someone do a start to finish howto for Hardy?

Much appreciated.

---

### Post by Paul7 on 2008-08-23
You should take a look at the Internet Connection Sharing Wiki

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Washer on 2008-08-24
Firestarter 4tw [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

