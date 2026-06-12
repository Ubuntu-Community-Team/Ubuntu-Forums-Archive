---
title: "Ubuntu Server - DNS problem?"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by Altrezia on 2007-09-23
Hello there,
Bit of a weird problem.
I installed Ubuntu Server on a laptop i had lying around, to learn the ropes, but I've run into a strange one. 

I have the network card set up correctly, and can ping everything internally. 

I can also ping google's IP.

I cannot ping by name, i.e. google.co.uk.

I was trying to install Symfony ([www.symfony-project.net](www.symfony-project.net)) but of course, this failed because I seem to have a DNS problem.

Anyone got any ideas for what could cause it? all my windows PCs work fine, and the laptop is plugged in by wire into my router, there are no special rules set up on it or anything like that.

Cheers,
Alex.

---

### Post by noob12 on 2007-09-25
Well what are you using for your DNS servers?

Typical issues are the ISP's servers are flaky or you have a router that serves as a local proxy DNS server, but it is buggy/unreliable.

Check out this thread, and if it doesn't address your issues post back here for some more specific diagnostic help:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by Altrezia on 2007-09-25
It was my fault - Checked the Resolv.conf and it has the wrong IP address.. god knows why.

Sorted now - and working fine. Cheers for the help

---

