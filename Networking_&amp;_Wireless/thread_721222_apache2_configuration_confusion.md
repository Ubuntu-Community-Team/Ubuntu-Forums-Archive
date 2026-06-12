---
title: "apache2 configuration confusion"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by dsbw on 2008-03-11
Hey, all:

   I'm having trouble setting up my Apache server (Gutsy), and it's a problem I've had before (under Windows, I think) but I can't remember how I solved it.

   I started with site1.com. All was well. I had a site2.com pointed to the same IP, so naturally, if you put in "site1.com" it would immediately turn into "site2.com" in your URL bar. Expected.

   Now I added in site2.com virtual host. The server's behavior doesn't change: If you put in "site2.com" in your browser, it would still turn into "site1.com". If I remove "site1.com" *completely* (disable the site, remove the entries from hosts and httpd.conf), I don't see site1 anymore, but the URL still reads "site1.com" (even though I'm now looking at site2.com).

   What the heck have I forgotten?

:redface:

---

### Post by BiggoCharley on 2008-03-14
I'm waiting with bated breath for a reply to your post -- I am having exactly the same problem.  I have tried everything I can think of and continue to have this problem.  I tried to run two apache installations --(apache 1.3 and apache 2.0--one serving "site1" and the other "site 2") side by side as a desperate measure but that didn't work.  I sure someone comes up with some ideas.

---

### Post by superprash2003 on 2008-03-14
this link should help [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) ..

---

### Post by dsbw on 2008-03-16
I ended up cheating. I installed ISPConfig and used that.

It seems to have worked, mostly, though I still sometimes find missed addresses on site2 going to site1.

I then abandoned ISPConfig because it's seriously clunky and makes some ugly configurations. I haven't figured out where it set things up, unfortunately, so I can't see what is different.

---

