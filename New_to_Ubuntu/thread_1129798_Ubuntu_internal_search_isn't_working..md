---
title: "Ubuntu internal search isn't working."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by CheetahDC on 2009-04-19
Okay, this is odd.  Now, after installing updates using the automated updater and restarting, the search feature within Ubuntu's internal Help Center on Gnome isn't working either.  I also installed ncds to clear my DNS cache, as I was having DNS issues with a certain piece of software.  What gives, and how can I fix it?

In the Ubuntu Help Center, when I search something, it gives me a list of results.  I then click on a result, then I am given a "Loading..." message...and well, nothing loads.  I try clicking on the result again, and the Help Center closes.

---

### Post by nandemonai on 2009-04-19
Well I'll be.. 

Are you using Jaunty? I just tested the help thing myself and it did the same thing.

Synaptic however does work.

You may have found a bug.

---

### Post by CheetahDC on 2009-04-19
I'm using Intrepid Ibex, 8.10.  Also, my mistake on the search in Synaptic Package Manager not working; that's working just fine, ignore that.  I just chalk the Synaptic Package Manager thing up to me being new to Ubuntu/GNOME/Linux.

---

### Post by nandemonai on 2009-04-19
Well I found some older bug reports on launchpad about this issue but no real recent ones.

There are apparently no open bugs for yelp in Intrepid but I've filed a report for Jaunty.

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/363633](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/363633)

Sorry I can't be of more assistance.

---

### Post by CheetahDC on 2009-04-19
How do I file a bug report for Intrepid Ibex?

Edit: Oddly enough, some searches like "bug" and "audio" work fine, but "DNS" does not and causes the constant Load and crash.

---

### Post by nandemonai on 2009-04-19
> **CheetahDC said:**
> How do I file a bug report for Intrepid Ibex?

Edit: Oddly enough, some searches like "bug" and "audio" work fine, but "DNS" does not and causes the constant Load and crash.

Create an account at [https://bugs.launchpad.net/](https://bugs.launchpad.net/) to file bug reports.

---

