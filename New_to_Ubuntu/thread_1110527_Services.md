---
title: "Services"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by mesmith on 2009-03-29
I'm running a Dell P4 with 1gb memory.  Would turning off some of Xubuntu's Services have any positive effect on speed and efficiency?  If so, what services could be turned off safely?  I noticed that alsa, keyboard stuff, bluetooth and a few others are of dubious value for me, but I don't want to break my system.  Or, should I just leave things alone?

Any help appreciated.

---

### Post by asmoore82 on 2009-03-29
I highly recommend the "Boot-Up Manager" for tweaking services/runlevels
```
sudo apt-get install bum
gksudo bum
```

It takes care to handle the init script soft links in the proper way.
The services-admin tool that ships with GNOME is completely broken in regard to this - not sure about Xubuntu.

---

### Post by Hospadar on 2009-03-29
I doubt that turning off services would really save much in terms of the performance/functionality ratio.  I've often found that when I try to do this I either notice no performance difference, or accidentally turn off something important that I want.

Due to the nature of services, they will pretty much stay blocked all the time and use almost no cpu time, and only a tiny slice of memory.  A p4 with 1gig should be able to handle xubuntu just fine.  That said, if you still want snappier performance or a really roaring boot time, you might want to try and just build your own desktop environment with something like fluxbox or openbox.  Try searching in the community docs in my sig, as I recall they have some great pages about setting up both.

These are very light window managers which, with a couple other utilities, can be built into a very fast and light desktop environment.  The advantage of building it yourself is you know exactly what is starting up at boot time and if you find something you are lacking, you can just go install it (although sometimes it can take a little research to figure out what you really need).

If you build it yourself, probably starting with an ubuntu server installation is the way to go.

---

### Post by mesmith on 2009-03-29
Thanks for the info.  Currently the only unchecked items are bluetooth (which I don't use) and audio settings management (alsa-utils).  Don't know what audio settings managemnt is for, but system seems fine without it.

---

