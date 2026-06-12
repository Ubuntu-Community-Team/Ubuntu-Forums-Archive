---
title: "Dmz"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Scorpuk on 2006-09-06
I am using my ubuntu box to run game servers, but I have ran out of slots to forward ports on my router so was thinking on moving it to the DMZ. I presume my game servers will work in the DMZ?


What are the implications of doing this?

Is Ubuntu strong enough to exist in the DMZ?

If the answer is no then can anyone suggest a router that will never run out of slots to forward ports on, ranged and single?


much obliged.

---

### Post by Rhubarb on 2006-09-06
Ubuntu should be strong enough to reside in the DMZ, if need be, you could install a firewall, such as firestarter.

I do however have a fairly limited knowledge of networking, I do understand port forwarding, but I haven't been able to find much info about DMZ.  So I'd also like to know! :-?

---

### Post by Scorpuk on 2006-09-06
Oh well one way to find out...


I'll stick my ubuntu box in the dmz and stop forwarding port 80. If my webserver stops responding I'll know.  lol :-k

---

### Post by Scorpuk on 2006-09-06
Looks like any computer placed in the DMZ will have all ports open and available to it.


Dissabled single port forwarding 80 and placed box in DMZ and I could still gain access to my webserver pages.


Will deff look into this when I get home from work. Until then router settings returned to as they were. ;)

---

### Post by tbonius on 2006-09-06
Why not hang it out on a DMZ and enable IPtables to only open ports you want to have access to?  Most NIX boxes if setup correctly should be sufficiently secure enough for most services if configured correctly.

-Shameless Plug-

[http://www.section6.net/wiki/index.php/Main_Page]("http://www.section6.net/wiki/index.php/Main_Page")

Many tutorials avaiable for configuring BSD as well as Linux

---

### Post by tturrisi on 2006-09-06
> **Scorpuk said:**
> Looks like any computer placed in the DMZ will have all ports open and available to it.

Dissabled single port forwarding 80 and placed box in DMZ and I could still gain access to my webserver pages.

Will deff look into this when I get home from work. Until then router settings returned to as they were. ;)
fyi - putting a comp in the dmz does this:  the router will pass wan requests to the comp in the dmz.  But that does not mean all ports on the comp are opened.  It means the only open ports on the comp are those ports used by certain applications or services such as port 80 for www server, 3036 for mysql, 10000 for phpmyadmin, etc.  If there are services on the comp listening on a port then for all the comp won't respond to unsolicited requests & for all intents & purposes no comp exixts at that ip from a wan viewpoint.

---

