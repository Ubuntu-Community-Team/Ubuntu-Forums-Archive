---
title: "Linksys Wireless router problems?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Master-of-None on 2008-01-20
Every so often my laptop refuses to connect, or connects for 5 seconds then hangs up. Is there, by chance, a problem with how Ubuntu handles Wireless Connections?

Another interesting fact: My modem(a cheap westel wired modem,) when reset, takes up to an hour to reconnect. Could this have anything to do with it?

Or might it be my router, a Linksys WRT54GC?

Whatever the reason it is, I'd like to figure out a way to fix my internet connectivity problems, as it gets on my nerves when both the Router, and my laptop, which were bought for me to use, don't cooperate.
:mad:

---

### Post by kevdog on 2008-01-20
Im guessing its probably a wireless driver issue.  What wireless driver are you using?

---

### Post by Master-of-None on 2008-01-20
I'm not entirely sure, in my hardware info it says RTL8187_Wireless. Am I in the right place? The Device Manager?

---

### Post by kevdog on 2008-01-20
No - that is correct.  If you do a 

lshw -C network

Is this device shown, 

if not
lspci

and if not

lsusb -v

---

### Post by Master-of-None on 2008-01-26
none of those commands you listed work.

---

### Post by Master-of-None on 2008-01-31
I've come to realize that the problem is with my laptop, and it seems to be a software, or driver problem. I LOOSE connections based on certain requests, such as posting in a forum, or updating my personal information. As I belong to quite a few forum communities, its impossible for me to do much of the things I used to, and oddly enough it seems the site range of which these incedents happen are growing. The one forum site I frequent a lot just started acting up today. I could no longer edit posts. If I don't get a quick solution soon, I may lose my ability to post on this site, as well.

---

