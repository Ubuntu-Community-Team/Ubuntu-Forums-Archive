---
title: "Question about multiple instances of processes"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by lastchancetosee on 2009-01-17
Hi,

can anyone tell me why so many programs open multiple instances of themselves?

For example:
I use opera. When opera is started, there are usually 3 instances of opera listed, all with different PIDs but identical PPID (1 = called from init? Which to me seems strange in and of itself) and memusage, only one of them uses CPU cycles.
Same with gnome-do, 5 instances called by PID1.
Miranda via Wine, 6 instances, PPID1
Same with other wine-related windows-stuff
/usr/sbin/apache2 -k start &#8594; 57! instances started with 3 different PPIDs
I don't even know what that one does.
and a few more.

I mean, what the hell? Why is there a process running (OK, sleeping :-) ) 57 times on my system?

OK, since for example all three opera-processes together are taking up more physical RAM than is installed on my system this is probably not a case of WYSISYG (or rather -H not -G) but still, I don't get it.

---

### Post by HermanAB on 2009-01-17
A browser does lots of things in parallel.  A typical web page consists of many bits of pieces of information assembled from different servers for photos, advertisements and the like. Many of these other machines can be slow and overloaded. By starting a separate thread for each, the aggregate user experience is better.

Cheers,

H.

---

### Post by lastchancetosee on 2009-01-19
OK, that makes sense. But shouldn't then thread B have thread A's PID as PPID?

Oh, I just noticed: When using tree-view in htop they are all listed as having one of their own as parent. So there seems to be an additional "Parent &#8594; Child"-identifier besides PPID I'm not aware of. Or PPID doesn't mean what I thought it meant ...

---

