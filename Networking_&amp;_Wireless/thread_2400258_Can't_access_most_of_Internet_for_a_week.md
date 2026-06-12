---
title: "Can't access most of Internet for a week"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by Torbjorn S.D. on 2018-09-04
Since a week ago I've been unable to access most of Internet. Some websites like Wikipedia, YouTube and Google work but most do not.

Several months ago I had similar troubles but eventually all started to work after a few days.

I have formatted my computer several times and reinstalled my OS several times but the problem remaines nevertheless. I run Ubuntu 18.04 Mate.

I've been troubleshooting using the ping command. Here are some results.

Ping Google.com - works perfectly.
Ping 8.8.8.8 - destination host unreachable.
Ping my gateway by IP - works perfectly.
Ping my dns server by IP provided by my ISP - 100% packet loss.

I'm writing this post from my smartphone and I'm beginning to panic. What should I do? Can someone please help me?

Best regards,
Torbjörn

---

### Post by aromo2 on 2018-09-04
You can run a traceroute to the troubling IP addresses. For instance:
```
traceroute 8.8.8.8
```
Probing a few different IP addresses should give you a hint of where the communication is breaking.
Hope that helps.

---

### Post by Torbjorn S.D. on 2018-09-04
I can't use tracerout because it's not installed and I can't install it because I can't access the Internet. :-(

---

### Post by MisterPi on 2018-09-04
Is your smartphone connected to the same router as your computer?  I assume you have some kind of router which connects to the Internet (via your ISP -- cable or FiOS or whatever).  Verify that your phone is actually going through the same router, rather than through the cell network.  (Sometimes if your phone can't get what it wants through wireless, it might revert to using the cell tower without telling you.)

You could also try moving your computer to a friend's house and trying that router.

It kind of sounds like a router issue to me, because you are able to reach SOME addresses.  Normally an end-point system is just configured to send all non-local packets to whatever it's connected to.  (Of course, it can be configured other ways, but I would expect a fresh install to be configured in the usual way.)

---

