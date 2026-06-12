---
title: "Why it take to long to load a page ?"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by taydu on 2008-01-24
I notice that i take around 30 - 45 second to completely load [www.yahoo.com](www.yahoo.com), [www.msn.com](www.msn.com) on Ubuntu while it only take 5 second max for it to load on Windows that running firefox?

I though it was the cache so i delete everything on both machine let it sit side by side and load [www.yahoo.com](www.yahoo.com) on ubuntu then load it on widnows, 5 second later windows already done, and ubutun still try to find yahoo.com

is this a common problem, any way to fix it ?

It really bug me :)

---

### Post by .nedberg on 2008-01-24
Both take about 1-2 sec here. I am using Opera though. It should not take longer in Linux. Someone else will have to help you with the why.

---

### Post by HermanAB on 2008-01-24
The most commonn cause is a lame DNS in /etc/resolv.conf.  If the first DNS is dead, then each request will cause a DNS timeout before it will try the next DNS.

On Windows, run c:>\ ipconfig /all

Compare the DNS settings with the contents of /etc/resolv.conf and change it if required.

Cheers,

Herman

---

### Post by taydu on 2008-01-24
the name server on windows and ubuntu look the same :(

Please help

BTW i wanted to install Opera, use this command sudo aptitude install opera now how do i run it and add a shortcut to application >>> internet 

thanks

---

### Post by .nedberg on 2008-01-24
> **taydu said:**
> the name server on windows and ubuntu look the same :(

Please help

BTW i wanted to install Opera, use this command sudo aptitude install opera now how do i run it and add a shortcut to application >>> internet 

thanks

It should be added to the menu. Else you can run "opera" in the terminal. I am using Kubuntu so I would noy know how to edit menus in Gnome...

---

### Post by y-lee on 2008-01-24
I always tweak firefox to achieve a faster speed, see [How to Speed up Mozilla firefox]("http://ubuntuforums.org/showthread.php?t=179540"),  also you might want to read the comments in [this forum]("http://www.terminally-incoherent.com/blog/forum/main/topic-4/?recent=64") as well as see the tweak here: [Speed up internet and google earth]("http://ubuntuforums.org/showthread.php?t=202838").

Also note[ Swiftweasel]("http://swiftweasel.tuxfamily.org/about.php") is much faster than firefox, but is a version of firefox just compiled to run faster. You can download a deb [here]("http://sourceforge.net/project/showfiles.php?group_id=195473").

---

### Post by taydu on 2008-01-24
try most of the tips non help, will try out Swiftweasel.

The problem is when i use the previous ubuntu it wasn't slow at all now using 7.10 it so slow

---

