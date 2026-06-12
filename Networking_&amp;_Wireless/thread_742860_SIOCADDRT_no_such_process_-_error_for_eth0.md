---
title: "SIOCADDRT: no such process - error for eth0"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by professor-g on 2008-04-02
32-bit ubuntu 7.10 installed on old PCs
have literally 40 of them noone cares for - setting up cluster
(PIV 1.4 GHz, 512MB, 40 GB HD)

cant get eth0 to come up!
get error:

SIOCADDRT: no such process
Failed to bring up eth0.

---

### Post by Iowan on 2008-04-02
What kind of network cards?
Post results of **lspci**and  **dmesg |grep eth**.
I'd ask about **ifconfig -a** and **/etc/network/interfaces**, but it seems like the card(s) aren't being detected.
(Gee, wish ANY of my computers were that "old" - my "fast" one is 800 MHz)

---

### Post by professor-g on 2008-04-03
Thanks for the help.
It was my 'absent mindedness' once again (requisite for professorship).
Seems gateway was mixed up and made no sense - overlooked this.

Just to let you know - yes ~40 'old PIV 1.4s' is nothing to complain about - agreed.
But they are not mine - I am merely setting them up here in one of the labs on my monthly pass through here at Hong Kong U.

Maybe we can arrange to send you some old computers - seeing that you are stuck with an 800 Mhz.
Let me know.

Thanks again for the help,


G.

---

