---
title: "Help troubleshooting a couple of boot messages?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by bgates on 2009-02-08
First of all, everything works.  I'm just trying to tune this so that only necessary things are loaded.  I have googled all of these, but it is difficult because it seems people only generally post these messages when they are actually preventing something from functioning, which isn't what I'm experiencing.

The first "issue" I get at boot is that hub 3-0:1.0 failed to enumerate on port 1.  All of the USB ports seem to work normally, but I only have USB 2 devices to try them with.  I think this message is because it is trying to enumerate USB 2 first, and USB 1 second, but I am unsure where I can change the order of this.  Alternatively, if I could disable USB 1, that'd probably work, as I have no devices that need to use it.

Then there is: "CPU frequency scaling not supported."  This might be because of my hardware, but is there a way to tell Ubuntu not to look for the scaling then?  

One other thing I noticed is that acpid is not being stopped at shutdown, until Ubuntu says "Asking all remaining processes to terminate" and then it does exit.  Should it have its own shutdown?  How could I fix that?

Thanks for any insight and help!

---

### Post by yeats on 2009-02-09
So to be clear, you aren't having any functionality issues, but are seeing these messages at startup (these are also recorded in /var/log/messages, fyi)?  If so, I wouldn't worry too much until something you're trying to use won't work. . .  

Of course, if something's not working, post back about that, but I wouldn't fret too much about the messages you're getting. :-)

Ubuntu/Debian/Linux is good at loading only what's needed by default . . . are you facing a slow startup?

---

### Post by bgates on 2009-02-09
Correct, everything works.  If I tried to use a USB 1 device on that particular port, then that might not work.  But I don't have any USB 1 devices.  So I would just as soon not load it if it's going to make an error and I don't need it anyway.  :)

I wouldn't call the startup slow, but I'd like to get it as fast as possible.  It's a netbook that is used mostly for whipping out to take notes on, so the faster it boots the more useful it is.  I'm way less interested in the boot time of my desktop.  I don't like using suspend and hibernate, for some reason I have always personally had issues with them no matter what machine it's on.

Thanks for the reply!

---

