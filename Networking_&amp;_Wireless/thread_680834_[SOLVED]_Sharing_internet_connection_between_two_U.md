---
title: "[SOLVED] Sharing internet connection between two Ubuntu PCs"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by JamesDS on 2008-01-28
Hey, was wondering if someone could advise me on this rather simple problem.

I have 2 Ubuntu machines, my laptop, and my brother's desktop.  I have Gutsy, he has Feisty.  I want to share my wireless internet connection with him, via our crossover cable, so he can upgrade.

How do I go about doing this?
[I]
Just on the side, I'm very happy with the last two releases of Ubuntu for being able to recognise my broadcom 43xx wireless card and give me immediate wireless access!  Well done Ubuntu developers :).  And, Gutsy supports much better ATI graphics drivers for my radeon xpress.   :D[/I]

---

### Post by hahahan on 2008-01-28
You can install firestarter, ubuntu's firewall. It has a option to do NAT routing.

Regards.

---

### Post by JamesDS on 2008-01-28
Do I require this on both machines, or just on the one connected directly to the Internet?

---

### Post by hahahan on 2008-01-28
Just the one thats connected to the internet.
For your interrest, take a look at the [http://www.tldp.org](http://www.tldp.org) and search for network & masquerading.

---

### Post by JamesDS on 2008-01-28
Thanks, I'll take a look at that.  This firewall looks hopeful, but it won't start, saying that eth0 (wired) isn't ready - what must I do to make it ready?  I currently have it configured as DCHP, and enabled in the Networking preferences.

---

### Post by hahahan on 2008-01-28
Sorry, can't help you with that, i have no firewall activated since i'am already behind a filtering router.
For setting up a router you'll better make the networkcard static, it's going to be the gateway for the second machine. I'll advice again doing some reading for a better understanding of networks. 

Have fun.

---

### Post by JamesDS on 2008-01-28
Thanks for your help, it's up and working :)

---

