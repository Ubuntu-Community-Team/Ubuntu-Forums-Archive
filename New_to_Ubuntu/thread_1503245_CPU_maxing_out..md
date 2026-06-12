---
title: "CPU maxing out."
date: 2010-06-06
forum: New to Ubuntu
---

### Post by uRock on 2010-06-06
HTOP reveals an app pegging out my CPU. This has happened more than once with the same app. Does anyone know what is causing this and how to stop it?

---

### Post by irongreatwall on 2010-06-06
I think its upgrading the system in the background... 
Does Ubuntu upgrade package using python?

---

### Post by ibuclaw on 2010-06-06
Looks like a daily cronjob to me. Updating APT's plugin index.

It's not the only cronjob that pegs it out on your system when you least expect it to. Updatedb does a pretty good job at doing that too. ;)

---

### Post by uRock on 2010-06-06
Thanx for the replies. Should disabling "Check for updates" in Software Sources fix this?

Thanx again,
uRock

---

### Post by ibuclaw on 2010-06-06
> **uRock said:**
> Thanx for the replies. Should disabling "Check for updates" in Software Sources fix this?

Thanx again,
uRock

Nope, uninstalling apt-xapian-index would stop it though.


Suggest you should read about what it does first though before doing so. [http://www.enricozini.org/sw/apt-xapian-index/](http://www.enricozini.org/sw/apt-xapian-index/)

It's not essential, but probably has a use for something you take for granted (Debtags, most notably - if at all you use to search for packages).

Reasons for you to keep the package:
synaptic Recommends apt-xapian-index

Regards

---

### Post by uRock on 2010-06-06
Thanx ibuclaw I'll check it out.

---

### Post by uRock on 2010-06-06
After reading about what it does I think it would be god to keep around. after running the ***history*** command I can see I have only had to kill python twice since installing Lucid, there is no need to remove it at this time.

Thanks again for the help,
uRock

---

### Post by ibuclaw on 2010-06-06
> **uRock said:**
> After reading about what it does I think it would be god to keep around. after running the ***history*** command I can see I have only had to kill python twice since installing Lucid, there is no need to remove it at this time.

Thanks again for the help,
uRock

No probs, as I said, it is not the only one that you may bump into. Once my system went into a state of stutter when in the middle of watching a film on iplayer. Turns out UpdateDB was scanning the entire filesystem to update the locate database. Bad bad timing for that. ;)

Cron jobs, can't live with them, can't live without them!

---

### Post by jwillar on 2010-07-06
This may relate to your problem.  My system (ubuntu 10.04) was pegging the CPU usage at 98%.  The problem would occur during and after running Firefox when viewing a video but would not occur when using Chromium.  I disable Compiz and kept the recomended video driver.  Continuing my troubleshooting, I discovered I had two plugings installed for FF for viewing streaming video (do not recall which).  After removing  one, I rebooted my system for good measure, launched FF and the video played w/o error and my CPU usage never exceeded 65%.  This seems to have resolved my problem.

Hope this helps, jwillar

---

### Post by ibuclaw on 2010-07-07
Thanks for your contribution, such a shame it is 4 weeks late.

Thread Closed.

---

