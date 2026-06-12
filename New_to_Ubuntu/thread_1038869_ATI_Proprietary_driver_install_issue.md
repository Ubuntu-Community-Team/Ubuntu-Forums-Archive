---
title: "ATI Proprietary driver install issue"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by bennis on 2009-01-14
So here is my problem. I open up the 'Hardware Drivers' section under System->Administration and it says that the driver I want enabled, isn't. There's a little button that says 'Activate,' I click it, a window pops up that says 'Downloading and installing' or some such thing, then promptly closes. No error output. Any ideas? Oh, and i'm using an ATI x1600 Viper.
Also, absolutely *no* idea how to change my resolution. Thanks.
Edit: Never mind about the installing the driver thing got that figured out.  Still, no idea how to change my resolution.

---

### Post by anewguy on 2009-01-14
Have you tried Envy?  Prior to 8.04 you use Envy, for 8.04 and 8.10 (the 2 newest) you use Envyng.  Just go into synaptic package manager and do a search on envy - it will be there.  When you start up Envy(ng), I would tell it to delete old drivers first, just in case what you have been doing has partially installed something.  I don't know off the top of my head if it supports your card (it does ATI or nVidia, but I think it also depends on the specific card).  You may want to check envy or envyng site to see if it says anything.  This is usually the first place to start for ATI or nVidia drivers, then chose a different route if this doesn't work.

dave ;)

---

### Post by newbee70 on 2009-01-14
> **bennis said:**
> So here is my problem.
Also, absolutely *no* idea how to change my resolution. Thanks.
Edit: Never mind about the installing the driver thing got that figured out.  Still, no idea how to change my resolution.

Have you gone into system / preferences / screen resolution?

---

### Post by bennis on 2009-01-14
Thank you both. I looked under System and totally didn't see it. A couple minutes ago i was pestering my mentors, and had deja vu. I remembered doing this before. So, now i know again. Thank you for the direction towards envy. I will check it out and post back if something goes wrong. Else, assume all is good.

Edit: So. Envy is currently incompatible with 8.10? I checked the standard software repositories and i found nothing. Should i be downloading a modified version?

---

### Post by peakshysteria on 2009-01-14
You don't state your OS. Follow one of the guides you find [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide"). These guides have been the most successful for me with the latest releases. Try this before you jump Envy.

---

### Post by anewguy on 2009-01-14
> **bennis said:**
> Thank you both. I looked under System and totally didn't see it. A couple minutes ago i was pestering my mentors, and had deja vu. I remembered doing this before. So, now i know again. Thank you for the direction towards envy. I will check it out and post back if something goes wrong. Else, assume all is good.

Edit: So. Envy is currently incompatible with 8.10? I checked the standard software repositories and i found nothing. Should i be downloading a modified version?

Yes, just use envyng - should be in synaptic package manager.

Dave ;)

---

### Post by bennis on 2009-01-14
Awesome. Found it, installing now. I can't seem to find the 'Solved' feature though. I looked in the thread tools. Am i just blind?

---

### Post by zika on 2009-01-14
no, due to problems in UF database [solved] and "thank" are disabled temporarily ...

---

### Post by peakshysteria on 2009-01-14
> **peakshysteria said:**
> You don't state your OS. Follow one of the guides you find [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide"). These guides have been the most successful for me with the latest releases. Try this before you jump Envy.

So how did it go?

---

### Post by bennis on 2009-01-17
It went well. There seems to be a bug, but a managable one. Everytime a download a certain update (not sure what) i have to uninstall and reinstall the driver. Its not a big deal, as ubuntu boots faster than vista. Thanks for all your help

---

### Post by peakshysteria on 2009-01-17
Mark this thread as solved and make another thread for this (new) problem. It shouldn't be this way at all. My Intrepid works close to flawless at the moment. People might solves this problem for you and people with the same problem.

---

