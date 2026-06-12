---
title: "Install a package from Karmic on Jaunty?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by jeffers.r on 2010-01-20
I'm relatively new to Linux, but certainly making progress on my skills. Nonetheless, this particular task is really stumping me up.

Here's the scoop, I tried upgrading to Xubuntu 9.10, but enough annoyances had me returning to 9.04 where I think I'll stay for the time being. Only catch is, I started using k9copy while in Karmic only to find upon my return to Jaunty that the version included with Jaunty is full of bugs and doesn't perform as needed. After some research, I was able to conclude that I need k9copy 2.3.2 at the very least to fix the bug I'm encountering, or preferably 2.3.3 which is included with Karmic. Currently Jaunty only includes k9copy 2.3.0.

So my question is this ... how do I go about getting k9copy 2.3.3 on Jaunty? Some things I've tried:

1. I found a deb package for k9copy:2.3.3 but then ran into a nightmare trying to find the necessary dependencies and finding deb packages for those, etc. There must be an easier way?

2. I tried using a PPA ([here]("https://launchpad.net/%7Emieszkoslusarczyk/+archive/kde4-extras-kde4.3")), only to find on further inspection that the k9copy package within this PPA [failed to build]("https://launchpad.net/%7Emieszkoslusarczyk/+archive/kde4-extras-kde4.3/+build/1175066") and as such isn't included within synaptic even though most of the others are in the PPA are.

3. I downloaded the source, but compiling using cmake required a KDE build environment and how to fix this up went way over my head.

Is there some means of getting this to happen?

Many thanks!

---

### Post by Swab on 2010-01-20
Not sure if they Backports guys do stuff from Multiverse or not.  You could try to convince them to backport.

[URL="https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages"]
https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages[/URL]

---

### Post by dearingj on 2010-01-20
Have a look at this page:
[http://packages.ubuntu.com/karmic/k9copy](http://packages.ubuntu.com/karmic/k9copy)

There you can find a deb package for Karmic's version of k9copy, as well as links to debs of all of its dependencies.

---

### Post by jeffers.r on 2010-01-20
Hey folks!

Swab: from the looks of things, they won't do backports for bug fixes anyway, which this essentially is. The package needs to have undergone some major upgrades. For bug fixes it directs me to the Stable Release Updates instead, which also appears to have some strict guidelines. But I'll explore both of those in more detail!

dearingj: I might have to go this route, but I was honestly hoping to avoid it. It seems that every dependency that I update then has another set of dependencies to update, and yet another set, and so on. So that's basically what I was doing in #1 but it was becoming a bit nightmarish so I was wondering if there was a better way that I was overlooking. Certainly not something I'd want to do often!

Thanks for the input! I'll keep working on this and see where it gets me.

---

### Post by achase79 on 2010-01-20
could you find a ppa that has that version made for jaunty.  I would search launchpad for a ppa

---

### Post by spongypants23 on 2010-01-20
You say your pretty new to Linux, but have you considered compiling it from source? There's bound to be a How To for compiling around here somewhere.

---

### Post by snowpine on 2010-01-20
According to packages.ubuntu.com, k9copy depends on core KDE packages. So, unless you  have updated your entire KDE desktop environment to the Karmic version, you aren't going to be able to install k9copy from the Karmic repositories.

---

### Post by jeffers.r on 2010-01-20
> **snowpine said:**
> According to packages.ubuntu.com, k9copy depends on core KDE packages. So, unless you  have updated your entire KDE desktop environment to the Karmic version, you aren't going to be able to install k9copy from the Karmic repositories.

I was wondering if that was the case. So here's where I get a little confused. I'm running XFCE, but naturally I can run KDE packages (such as k9copy) anyway. Is there a way to update the KDE environment packages that are included with Xubuntu 9.04 to the next version of KDE without upgrading my entire Xubuntu release itself?

I know how to install the entire KDE (or Kubuntu) desktop, but that still didn't use the latest version, and I'd rather not install the entire thing if I don't have to. It changes some aspects of the boot, etc.

---

### Post by jeffers.r on 2010-01-23
For what it's worth, what I ended up doing in order to get the latest copy of k9copy on Jaunty was add the Karmic repositories, perform the update, and then uncheck those same repositories so that I didn't get upgrades to anything else that I didn't want.

In other words, I opened Synaptic > Settings > Repositories and then added to the Third-Party Software sources:
```

deb http://archive.ubuntu.com/ubuntu karmic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu karmic main restricted universe multiverse
```After this, I reloaded the package list within Synaptic, update k9copy, and then unchecked those new repositories to prevent any other "accidental" updates.

What implications this may have on other software, I've yet to determine, but so far so good for those particular packages.

Hope that helps if anyone else is trying something similar.

---

