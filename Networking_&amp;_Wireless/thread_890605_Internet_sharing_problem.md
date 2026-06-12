---
title: "Internet sharing problem"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by michaelkahl on 2008-08-15
I run Ubuntu at work (currently 32bit) but I have 2 extra hdd's that I've been setting 64bit up on(I figure it's best not to break something that works till I have a full working replacement).  Anyway I have two nic's eth0 and eth1.  eth0 is connected to the network at work, eth1 is connected to my windows laptop that I occasionally remote into for Visio.  On my 32bit installation I followed this guide,
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
Everything worked with no issues.  In fact at that time I tested it by joining my laptop to the domain through the ubuntu box.  
Now to my 64bit experience.  I got everything working except for this one thing.  When I follow the above guide it works, but as soon as I reboot the system I have to run**# dpkg-reconfigure ipmasq**  in order to get the internet working on either machine.  When reconfiguring ipmasq I have tried all various options with no luck.  If anyone has any insight please feel free to share, I don't need 64bit, but it'd be nice to take advantage of all 4gb of memory I'm running.
Thanks

---

### Post by michaelkahl on 2008-08-15
Also I thought I'd point out that my internet is coming in from a 172 network(eht0) while the laptop connects via a 192 network (eth1).

---

### Post by SpaceTeddy on 2008-08-15
mhm - this sounds as if ipmasq is not loaded upon boot. Check this in your /etc/rc2.d folder. There should be a link like S20ipmasq in there (i think).

Also - a 32 bit system can use 4 Gb of ram. 2^32 is 4Gbyte. Even if you have more the 32-bit ubuntu server is able to handle more than 4Gbyte or ram - the only limitation is that one process cannot allocate more than 4 Gbyte. Hardly a drawback.

Just out of curiosity - what do you need 4Gbyte of ram for ? what application are you running ?

hope it helps :)

---

### Post by michaelkahl on 2008-08-15
Honestly I need 4gb of ram at work for nothing in particular, the machine has it but only reports 3gb in ubuntu. I'm not ever sure I've broken 1.5gb of system memory during my most intense use.
Later on down the road I may be hosting virtual machines on the system, but we'll see. 
As for ipmasq not starting I'll check that out.
Thanks for the reply.

---

