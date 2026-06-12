---
title: "HowTo SOHOware ethernet card"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by gscratch on 2010-08-25
I am running 10.04 on a 'generic' machine. Winfast mb AMD chip (I can provide more details if it is relevant). the system has been running fine for several weeks.
 
after a recent power failure, I no longer have any Ethernet connectivity. The Ethernet port is integral to the mb. the link light is on but the yellow light is also on steady. the cable and hub ports work with other systems, so I assume that the Ethernet port is done.
 
I have an old Intel ethernet card, model 721383 but I don't find any Linux drivers for it on Intel's site
 
I have a SOHOware sfa110a PCI ethernet card. From this page
[http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm](http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm)
I downloaded both a tulip.c file and a zip file containing several files. That same page has instructions for installing the drivers.
 
I have installed the hardware in the machine and powered it on. the link light is on when I connect to my hub.
 
Please point me to instructions for getting this network card working, or suggest that I use the Intel card, or something completely different. The only reference to the SOHOware card that I find in the forums, is in a forum that I don't have rights to post. In that post, the card was already working at 10Mb, so it didn't help me
 
thanks,
Glen

---

### Post by gscratch on 2010-08-29
Well, it works.  I got no replies to this post and tried a few other things, none of which worked

I booted the Live CD (my thought was to see if there was a 'repair network' or something).  Oddly enough, running off the Live CD, my embedded ethernet port worked.  So, falling back on my Windows experience,  I reinstalled, destroying the existing system, and now my ethernet works.

perhaps a driver got corrupted?

anyway, I'm back.  I'll mark this one 'solved' although I don't think I can recommend a nuke & pave as a solution.
Glen

---

