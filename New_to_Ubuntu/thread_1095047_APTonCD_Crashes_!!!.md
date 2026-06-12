---
title: "APTonCD Crashes !!!"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by abybaddi on 2009-03-13
I opened APTonCD, clicked on create, It reads information of packages...
Loads 30% and then closes.

What the hel! How should I overcome this?

---

### Post by abybaddi on 2009-03-13
Here's what I get, when I do that from terminal:

abybaddi009@abybaddi009-desktop:~$ aptoncd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
FATAL -> Failed to fork.
abybaddi009@abybaddi009-desktop:~$

---

### Post by mikechant on 2009-03-13
Looks like you might have hit this known bug:
[https://bugs.launchpad.net/aptoncd/+bug/272509](https://bugs.launchpad.net/aptoncd/+bug/272509)

Although some of the comments say it's fixed, if you read all the way through I don't think it is, and the bug status is still 'in progress'

---

### Post by abybaddi on 2009-03-13
I can neither get the head nor the tail of what they have written.

---

### Post by mikechant on 2009-03-13
> I can neither get the head nor the tail of what they have written.

I don't think it's important. What matters is that this appears to be a known bug, it's in the process of being fixed. 

There was a suggestion (not followed up) that it might be to do with the number of packages involved, so depending what you're doing you might get it to work if you select subsets of the packages you want - i.e. split it up into several operations; but I don't know if that's practical for what you want to do.

---

### Post by robinparriath on 2009-03-14
Hi abybaddi,

I had the same problem and I got it fixed when I did a clean install of the aptoncd_0.1.98-0ubuntu4_all, available from:

[http://launchpadlibrarian.net/18476205/aptoncd_0.1.98-0ubuntu4_all.deb]("Debian Package aptoncd_0.1.98-0ubuntu4_all")

It is a gdebi install.(Just double click on it after downloading to start installation)

Please note that this is not available from the Ubuntu repositories and hence considered 'fix in progress'... but it works with Ubuntu 8.10 Interpid Ibex(that's my system).  Do let me know it fixes it for you.

Many thanks mikechant for the thread link.  That's where I got the fix!

---

### Post by abybaddi on 2009-03-14
> **robinparriath said:**
> 
[http://launchpadlibrarian.net/18476205/aptoncd_0.1.98-0ubuntu4_all.deb]("Debian Package aptoncd_0.1.98-0ubuntu4_all")


Yes, this works for me. But do I have to download all the packages that I've installed? No packages show up in the list.

---

