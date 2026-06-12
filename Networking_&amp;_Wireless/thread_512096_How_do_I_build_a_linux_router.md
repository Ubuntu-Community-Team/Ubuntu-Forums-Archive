---
title: "How do I build a linux router?"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by tuprox on 2007-07-28
My Linksys WRT54G just crapped out on me. I unplugged it to test an identical router, now the power light flashes non-stop (any ideas on this?).  I figured I'd try setting up a router with an extra P3 I have sitting around.  It has 2 NIC's and I am going to purchase a wireless card down the road, but it isn't necessary now.

I'm sure there are guides but I have been unable to find them.  If anyone knows of a good guide, I would greatly appreciate a link.  

I would also like to setup this machine to be a webserver/fileserver/router.  Any suggestions on the best setup for this?  

I am planning on running 6.06 (desktop or server, I'm not sure which yet) unless someone can give me a reason why I should use 6.10 or 7.04 (I have 6-7 months experience with 6.10 server)..

Thanks for any help you can lend!

---

### Post by dannyboy1121 on 2007-07-28
Perhaps this will help ...

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

### Post by mckenzie on 2007-07-28
I currently use smoothwall as my router/gateway, but it doesnt do webserving/fileserving. However, in the past I have used SME Server [http://www.smeserver.org]("http://www.smeserver.org") Which easily allows you to have multiple "websites" and I think it may automatically update a dyndns accout. If you are looking for a ubuntu solution, you can install ISPConfig [http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704") which allows you to graphically setup websites. there is also ebox [http://ebox-platform.com/]("http://ebox-platform.com/") , but im not sure how it works on ubuntu (I run gutsy and the gutsy repos only have a few ebox modules

---

### Post by tuprox on 2007-07-28
> **dannyboy1121 said:**
> Perhaps this will help ...

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

This is what I am looking for.  I was wondering if anyone had a guide to do it with 6.06 server or desktop?

---

### Post by matthew on 2007-07-28
> **tuprox said:**
> My Linksys WRT54G just crapped out on me. I unplugged it to test an identical router, now the power light flashes non-stop (any ideas on this?).!
It looks like others have already helped with the other issues. I have the same router (running dd-wrt firmware now days). It has exhibited this behavior when it isn't getting the right voltage. Check and see if your power supply has gone bad.

---

### Post by tuprox on 2007-07-29
> **matthew said:**
> It looks like others have already helped with the other issues. I have the same router (running dd-wrt firmware now days). It has exhibited this behavior when it isn't getting the right voltage. Check and see if your power supply has gone bad.

thanks for the info, that makes a lot of sense.  The only thing that I changed with the router was disconnect the power supply then reconnect it.  How did you fix your issue?

---

### Post by ayenack on 2007-07-29
If you haven't already and your router has a reset switch try resetting, might do the trick. Normally have to hold it in for ten seconds or so.

---

### Post by matthew on 2007-07-29
> **tuprox said:**
> thanks for the info, that makes a lot of sense.  The only thing that I changed with the router was disconnect the power supply then reconnect it.  How did you fix your issue?Exactly what you did...early on. Later I had to buy a replacement power supply. It's a relatively common voltage/plug type, so I found an off-the-shelf model that works fine.

---

### Post by tuprox on 2007-07-29
I've tried the reset switch, for up to 30 seconds.  BTW, I'm running DD-WRT23 on this router as well, I wonder if that could have anything to do with it.  I'll try another power supply, hopefully that should do the trick.

---

### Post by tuprox on 2007-07-29
> **dannyboy1121 said:**
> Perhaps this will help ...

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

I've been trying to follow this article but it is a little vague in a few area's.  Does anyone know of a way to build on without webmin?

---

