---
title: "Firefox Not Browsing in Ubuntu 9.04"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Kalukis on 2009-06-27
I've seen some posts similar to this but...
 
I'm trying to learn Ubuntu; I've pretty familar with the Windows world and I used UNIX a long, long (pre-GUI) time ago.
 
Now I'm doing this in VmWare virtual environment, but I got the same problem in Microsoft's Virtual PC, so I think it's somewhere in Firebox and/or Ubuntu.
 
I've got the IP connection working, so I can ping external websites.
 
When I bring up Firebox 3.0.10, it comes up ok, but when I try and browse a website (like [www.ubuntu.com]("http://www.ubuntu.com"), [www.yahoo.com]("http://www.yahoo.com"), etc.), I get a delay and then a connection timeout. I've disabled IPv6 in Firevox, but that didn't help.  These are the same websites that I can ping from the command line.
 
Any rational ideas would be appreciated.
 
-Kalukis

---

### Post by philcamlin on 2009-06-27
is your internet connected 

you can see in the top right :popcorn:

---

### Post by ELFMAN69 on 2009-06-27
> **philcamlin said:**
> is your internet connected 

you can see in the top right :popcorn:
it would have to be connected for him to ping the site, right.

---

### Post by izizzle on 2009-06-27
You might want to check Firefox's proxy settings and make sure they are set up accordingly.

---

### Post by Kalukis on 2009-07-02
> **izizzle said:**
> You might want to check Firefox's proxy settings and make sure they are set up accordingly.
 
According to what?

---

### Post by eentrepreneur on 2009-07-08
Well i believe i had a similar problem. i think the root cause of the problem is with the configuartyion of the network relationship on vmware. what i did was bridge the network adapter from the hardware setting on vmware from host only and that did it. so u can try it.. You can check the network relationship summary on the lower left corner of the vmware enviroment..cheers and hope that solves ur problem....

---

