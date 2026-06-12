---
title: "swap usage log"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by infestor on 2009-10-12
[LIST=1]
[*]how can i see a log of my swap usage over time?
[*]i have 3 GB RAM installed on my PC, at present i have 3 GB swap reserved; should i increase the swap partition to 6 GB?
[/LIST]

---

### Post by mcduck on 2009-10-12
Without even using any tool I can pretty accurately tell that you are using somewhere between 0 and 100MB of swap. :D

You have plenty of RAM, it's unlikely that you'd ever rally need swap apart from the minor swap use that Linux uses to determine if something should be dropped completely from memory or if it should still be kept in cache.

I can't right now think of any program to monitor swap use over time (mostly because "0" over long time is not very interesting thing to monitor :D), but running "free -m" in a terminal will tell you your current RAM & swap usage.


edit: I highly doubt that increasing your swap space would make any difference to you. Swapping is something that you usually want to avoid at all costs, and like I said above, you are most likely hardly even touching your current swap.

---

### Post by kanikilu on 2009-10-12
You can use [**vmstat**](http://linux.die.net/man/8/vmstat) and it's "delay" and "count" options to get a look at usage over time.

---

### Post by infestor on 2009-10-12
@[mcduck]("http://ubuntuforums.org/member.php?u=17309")
thanks for the explanation.
but how come some applications are running slower than winxp (32bit)? like netbeans and firefox. they require more time to startup and freeze for short time preriods while using. is it because i use 64bit version of ubuntu 9.04?

---

### Post by Penguin Guy on 2009-10-12
> **infestor said:**
> @[mcduck]("http://ubuntuforums.org/member.php?u=17309")
thanks for the explanation.
but how come some applications are running slower than winxp (32bit)? like netbeans and firefox. they require more time to startup and freeze for short time preriods while using. is it because i use 64bit version of ubuntu 9.04?
I don't know about Netbeans, but Firefox was designed for Windows, and therefore it, of course, works better on Windows. If you want a faster web browser you should try Epiphany, although you won't be able to install Firefox addons.

---

### Post by mcduck on 2009-10-12
Startup times can't really be compared between operating systems because things work in very different ways even if the programs are same. For example the way graphical desktop is handled in Linux is way more complicated than in Windows, and while that brings a lot of more flexin´bility and features it also results in slightly less responsivity in the user interface.

I have no idea about your Firefox periodically freezing. I've never experienced such thing. Could be related to some extension you are using, or perhaps your graphics card drivers or something.

But I can definitely tell you that using more swap wouldn't help a bit, swapping doesn't improve performance, it's only used as last possible solution in cases when your system simply doesn't have enough RAM to do what it needs to do, and will always result in very bad performance. Hard drives are roughly thousand times slower than your RAM is, so using the disk instead of RAM isn't something you'd ever want to happen.

---

### Post by infestor on 2009-10-12
again, thx a lot guys :)

---

