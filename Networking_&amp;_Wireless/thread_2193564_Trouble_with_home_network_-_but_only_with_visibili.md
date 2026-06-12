---
title: "Trouble with home network - but only with visibility"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2013-12-13
Hi,

I could use some help with this one...  

_Here's my home network configuration:_
Desktop PC running Windows 7 premium, wireless Toshiba laptop running Ubuntu 12.04 32bit, wireless Lenovo T61 laptop running Ubuntu 13.10 64bit

_Here's what happens:_  
1. all three computers are successfully on the home network because they can all access the internet just fine.

_Here's what's weird:_
1. the two laptops can each see the Windows 7 computer on the network but cannot see each other.
2. the windows 7 desktop cannot see the two laptops on the network.
3. I've installed Samba on each laptop and configured various folders for sharing and tried again - still not able to see anything

I'm really no expert with Ubuntu or home networking - can someone tell me what I can do in order to be able to share files amongst the three machines?

Thanks

---

### Post by ub-newbie on 2013-12-13
A few questions to get us started.
1.  Can you "ping" from each computer to all of the others?
2.  What are your firewall settings on each computer?
   2.a. In Win 7 you are looking for "File and Printer Sharing".
   2.b. In Ubuntu try "sudo iptables -L -n" 
3. In your router, is the Wired and Wireless network bridged? (Q.1 should also answer this, but a double-check is always good).
4. Are you wireless clients "isolated" in your router? (again,Q.1 should answer this, but ....)

Once we figure out who can ping whom, we will know if they are able talk to each other on the most basic level.  Then we look at what might be stopping to Samba connections (i.e. Firewalls), then we will look at Samba itself.

---

### Post by drumkitcat on 2013-12-16
Thanks I will check on these things and get back to you this week.

---

