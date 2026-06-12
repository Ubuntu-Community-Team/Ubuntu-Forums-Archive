---
title: "Laptop powers down automatically"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-06-01
So, I'll be using my computer and suddenly the laptop will shut down, with NO warning whatsoever. Its almost like a windows virus.

The only thing I can imagine is that it is getting too hot. Otherwise my usage has not changed (temperature where I live has gone up quite a bit).

Sometimes it shuts down properly (with the shutdown screen, etc.). And other times it just goes black and off.

Has this happened to anyone?

Using jaunty on a laptop.

---

### Post by wpshooter on 2009-06-01
Get some kind of fan unit and let it blow as directly as possible on the laptop while it is running and if it no longer shuts down unexpectedly then problem solved, you have an overheating problem.  

But somehow, I have my doubts that this is an overheating problem.  When did the problem start ?  Was it roughly after the time that you installed/started using Jaunty ?

---

### Post by abhiroopb on 2009-06-01
Fan is pretty much not an option unfortunately. I'm in university dorms and we're not allowed them, and even if we were I've had a look and they're quite pricey. Anyway I guess I can get one but only if it seems thats the problem.

Can't put my fingure on exact time, but definitely after installing jaunty (i.e. didn't happen AT ALL with hardy). But then its only in the last few days that its gotten really hot (as in the general temperature).

I checked HD Temp: and thats 61C
CPU temp seems to be 65...

Yikes I guess I found my problem!

BEst keep it off for a while

---

### Post by wpshooter on 2009-06-01
Do you have any other O/S on this computer (like M/S windows).  If so, does it shutdown when running that O/S ?

---

### Post by abhiroopb on 2009-06-01
Unfortunately I'm ubuntu all the way!!

---

### Post by wpshooter on 2009-06-01
> **abhiroopb said:**
> Unfortunately I'm ubuntu all the way!!

Stick the live Ubuntu CD in the machine and let it run off of the CD for a good while and see if it does the same thing.  If it does shutdown, then "perhaps" you have a heating problem.  But if not, then "perhaps" you have an O/S installation problem.

---

### Post by Mark Phelps on 2009-06-01
Would also suggest you try an "older" LiveCD (Intrepid or Hardy) to see if the problem is related strictly to Jaunty.  Only mention that because I've seen a few posts in the forum from folks claiming that their machines now run HOT since they upgraded to 9.04.

---

### Post by steeleyuk on 2009-06-01
You could try a laptop cooler, they're not overly expensive.

---

### Post by abhiroopb on 2009-06-02
DO you have any links?

I think this might be temporary, a) because it rarely gets this hot, and b) first time in three years of living here that anything like this has happened.

HD and CPU temp at about 35C now...wow almost doubled yesterday!

Thanks for the help guys, but I'll ride it out for now. But yes I think its safe to say that jaunty is running much hotter.

Btw in my bios SATA native support is disabled. Should I enable this (my HD is SATA)?

---

### Post by abhiroopb on 2009-06-02
OK I think there is a major problem.

My HD starts of at about 31-32C and moves up to about 60C. Right now its about 56C. This really can't be normal. I guess I'll have to look into a fan of some sort, but I've never needed it before.

Could it be a result of a programme or something?

Any thoughts?

---

### Post by steeleyuk on 2009-06-02
I've seen people report that there computer is generating more heat when they've updated their distro. Often happens because of changes to drivers or ACPI.

If the temperature has gone up in Coventry as much as it has here, then its likely that the problems are being caused by that. I know my laptop has been running really hot as well recently.

There is a bunch of [laptop coolers here]("http://www.scan.co.uk/Index.aspx?NT=1-0-99-579-0"), not sure on how they perform but some Google searches should come up with reviews. Some people say that you should use a laptop cooler whenever possible anyway.

---

### Post by abhiroopb on 2009-06-02
Yes, Coventry has gone up a lot!

I guess I'll just use it at night :P!

---

### Post by abhiroopb on 2009-06-02
So, I left my computer off for about 12 hours, made sure it was completely cool extra.

Then plugged it in (without battery). Started using it. No seriously heavy usage. Downloading a few things, internet and music.

The temp of the HD starts of at about 30C, moving to about 38C in about 5-10mins. 30 mins into using it and the temp is now about 53C, rising by about a degree every few minutes.

I'm guessing it'll hit 60 and switch off again.

Its night here and relatively cool, so I don't think it is the external heat. Seems to be a problem with jaunty overheating.

Any thoughts? Have there been any known issues regarding this?

---

### Post by Boelcke on 2009-06-04
I don't have any answers, but thought I'd point you to this post, which refers to yours:

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

I've been considering upgrading my laptop, since I'm still on 7.10 (Gutsy).  Reading this by chance, however, has me considering leaving well enough alone for now.

Since I obviously lack the proper motivation, hopefully someone will come up with (and post about) a solution.  One that's not installing the old distro!

---

### Post by abhiroopb on 2009-06-05
Thanks for that, but actually if you notice, I started that post. As there were so many regarding this issue, I thought I'd just collate everything together. Unfortunately no convincing solutions yet!

---

