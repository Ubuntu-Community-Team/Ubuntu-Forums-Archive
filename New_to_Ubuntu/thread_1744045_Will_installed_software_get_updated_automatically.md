---
title: "Will installed software get updated automatically?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by spielball on 2011-04-30
Excuse me, I'm still a complete newbie. But I am willing to learn. :popcorn:

I have a simple question:

I just installed mkvtoolnix via packet manager. To my surprise, right  after I launched mkvtoolnix for the first time, it tells me that there's  an update available (v4.5.0 > v4.7.0). So I wonder if I have to  update the installed software manually from the author's website, or  will it be updated automatically at some point through Ubuntu's packet  manager?

---

### Post by beew on 2011-04-30
> **spielball said:**
> Excuse me, I'm still a complete newbie. But I am willing to learn. :popcorn:

I have a simple question:

I just installed mkvtoolnix via packet manager. To my surprise, right  after I launched mkvtoolnix for the first time, it tells me that there's  an update available (v4.5.0 > v4.7.0). So I wonder if I have to  update the installed software manually from the author's website, or  will it be updated automatically at some point through Ubuntu's packet  manager?

I think you mean V4.7.0 > V4.5.0. If you install from the Ubuntu repo you won't get any version upgrade in the next 6 months. Softwares in Ubuntu's repository are "frozen" in that you don't get feature or version updates between releases (with very few exceptions, Firefox being one) 

On the other hand  if you can find a ppa (third person repository) and install from it the versions will get updated though you have to wait, the wait may be short or long depending on the ppa. But you can install and upgrade through the package manager once you add the ppa to your sources list so it is preferable to manual install.

Found this ppa
[https://launchpad.net/~gilir/+archive/unstable]("https://launchpad.net/%7Egilir/+archive/unstable")

It is not the latest version but it will probably be updated later, whereas the Ubuntu version never will.

---

### Post by spielball on 2011-04-30
Thank you very much for this information. 6 months update interval is ok for me. Except for security relevant things, such as browser updates. But I take it that Firefox is being updated regularly?

---

### Post by andrew.46 on 2011-06-12
> **beew said:**
> Found this ppa
[https://launchpad.net/~gilir/+archive/unstable]("https://launchpad.net/%7Egilir/+archive/unstable")

Mind you the man responsible for mkvtoolnix runs his own repository:

[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu)

which might be worth looking at as this software is updated frequently, currently running at 4.8.0.

---

### Post by Toxicbits on 2011-06-12
Actually there are StableReleaseUpdates, but only if the Update fixes a severe security issue: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by VOT Productions on 2011-06-12
Basically, if you installed a program using Ubuntu repositories (Software Center, Synaptic or apt-get), you will get updates using Update Manager. If you compiled it, you won't get updates at all. If you downloaded a program from another repository (take Google Chrome as an example), you will get updates depending on the author.

---

