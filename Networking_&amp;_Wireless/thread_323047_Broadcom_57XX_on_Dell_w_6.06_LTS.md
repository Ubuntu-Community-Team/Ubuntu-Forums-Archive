---
title: "Broadcom 57XX on Dell w/ 6.06 LTS"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by moszer on 2006-12-21
Hello All, 

I just installed Ubuntu 6.06 on my new Dell Precision 390.  The integrated Broadcom 57xx gigabit controller doesn't appear to be working right after install.  

An lspci lists the card and when I run /etc/init.d/networking it says the interface doesn't exist.  

I did an lsmod and didn't see the bnx2 module loaded so I modprobed it and tried again, no dice.  In /etc/networking/interfaces it has eth0 set to auto and dhcp.  

I then went to dell's site and found they had a rpm for this card so I used alien to convert it over to a deb and installed that, which gave me the tg3 module.  I modprobed that and restarted networking, again no dice.  

It sure would be nice if I could see the kernel source to see what is in the kernel but...

Anyone know what give here?  Did I overlook something simple?  I see alot of other posts on this damn ethernet controller but none that made it this far and it still didn't work.  

Thanks!

---

### Post by moszer on 2006-12-21
Looks like it was a bug in 6.06, I downloaded and installed 6.10 and it works fine. 

FYI for anyone with the same problem.

---

