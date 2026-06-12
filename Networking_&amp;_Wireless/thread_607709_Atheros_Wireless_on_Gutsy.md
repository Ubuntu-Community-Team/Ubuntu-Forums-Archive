---
title: "Atheros Wireless on Gutsy"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by jr.gotti on 2007-11-09
I've had nothing but problems with wireless since "upgrading" to Gutsy. After posting a rather aggravation-driven post in the Testimonials section, I decided I didn't want to have to reinstall EVERYTHING, so I thought I'd give it a few more days to try and work it out.
 
After installing all the updates (I think libc and family had something to do with some of it,) I got the routers DHCP server to finally respond.
 
After typing ifup ath0, however, it does it's thing, I get assigned an IP, and it says reset in 2345245 or whatever. Everything looks as it should.
 
However, I can ping the other computers on the network. I can ping the router. Google? No dice. Yahoo? No dice. Internet? No dice.
 
How can this be? I can't think of any logical explanation except faulty router configuration. However, I reset the router. Same situatation. Any input would be beyond appreciated.
 
Thanks!
 
Jason

---

### Post by shruti on 2007-12-13
Same problem here - as my life practically depends on the Internet, I will be downgrading to Feisty for now. :( :confused: :mad: 

Just for the sake of trying, I tried a few LiveCD distros based on Gutsy (Linux Mint Daryna, Freespire...) with no success.  Is it a gutsy bug or a Linux kernel problem? :confused:

---

### Post by shruti on 2007-12-13
I forgot to mention, I also had trouble getting wireless working on my BRAND NEW (2 weeks old) HP Pavillion.  Maybe this is a wireless problem in general? (Does anyone know what chipset HP uses?)

---

### Post by jr.gotti on 2008-02-04
BUMP:: Anyone got a fix for this? I had it working, but for some reason had to reinstall gutsy...it got completely trashed. Now I'm back here. Everything connects fine, but I get no internet. I'll continue to look around and post back here if i find anything.

---

### Post by ounas on 2008-02-04
Have you tried installing wicd and madwifi, after removing network manager.

:guitar:

---

### Post by jr.gotti on 2008-02-04
Actually, it only took blacklisting ipv6 to solve my problem.

After that, it only took me 3 hours to realize my dad unplugged the wireless router last night. -.-

Moral of the story: Always check the simple stuff first.

---

### Post by ounas on 2008-02-05
Your right about that..

Rock on

:guitar:

---

