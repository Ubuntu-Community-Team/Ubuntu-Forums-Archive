---
title: "Intrepid: IP's no reverse order?"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by core on 2008-11-16
Hi all

When i've installed Ubuntu 8.10 on my laptop, i noticed i couldn't connect to my XP box via RDP. I was trying to use it's host name, let's say "xpto".

It's internal IP Address should be 192.168.1.1. Then, trying to ping, i noticed the problem:

myself@mylap:~$ ping xpto
PING xpto (1.1.168.192) 56(84) bytes of data.

So I try 192.168.1.1 on RDP, and the it worked. Why is the machine's IP addess reversed? What could cause it? What could it be for?

We have a Vista laptop here, and a ping to "xpto" returns responses from 192.168.1.1 right away.

I'm no expert on networking - not even close actually - maybe this is somehow normal on some networks, but it doesn't make any sense to me.

Any ideas on this? Something Ubuntu does while handling Windows networks I should know about?

Thanks.

---

