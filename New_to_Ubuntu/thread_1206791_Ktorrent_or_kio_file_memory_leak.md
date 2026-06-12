---
title: "Ktorrent or kio file memory leak ???"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by obscur156 on 2009-07-07
Hi all,since last night,when using Ktorrent , i have KIO FILE eating up my memory like crazy.I can see it going up every second with system monitor.If i let it go for long time it will make my pc going to a crawl.

I have not installed anything new on my pc since yesterday but i remember that there was some security updates yesterday.Maybe its relataed to it, not sure.

Somebody have an idea?

Thanks ,best regards.

---

### Post by DonCasper on 2009-07-08
I'm not quite sure if ktorrent is necessarily causing the memory leak, though I know KIO has issues when there are large numbers of torrents on some trackers.  If you install ktorrent 3.2.2 you can choose to use ktorrent to announce rather than KIO.  That might help, but before I installed 3.2.2 I was running hundreds of torrents through KIO and it only used about 4 mb of RAM, of course none of my torrents were announcing correctly so who knows.  By the way, you have to compile 3.2.2 from source if you want to install it.

---

### Post by obscur156 on 2009-07-09
Thanks DonCasper for your reply.
Of course it was 3.2.1 build that i was using,i did not tried the 3.2.2 version yet.Maybe i will try it later.

Now i have removed every KDE apps that i had...

Using Transmission right now,nice simple and easy to use but not as nice GUI as Ktorrent.

Thanks again,best regards.):P

---

