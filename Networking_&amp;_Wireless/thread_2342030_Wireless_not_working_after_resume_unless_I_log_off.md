---
title: "Wireless not working after resume unless I log off"
date: 2016-11-03
forum: Networking &amp; Wireless
---

### Post by -NabLa- on 2016-11-03
Hey. Been puzzling for quite a while over this one. This started happening recently, around september on Ubuntu 16.04 and continued through to 16.10 after upgrading.

I've been having issues with networking not recovering after waking up from suspend. Network appears connected correctly and I see nothing untoward on the system logs. I cannot connect to anything at all. Restarting network manager or networking service doesn't help. 

This issue solves itself if I log off and log back in - not a reboot, but simply logging off back to the Unity greeter. Inspecting logs I can see network hasn't been reconnected when logging off and then back on again. The only change is logging off my user account and logging back in.

Something similar happens with the ethernet connection, but instead of after a resume it happens after I unplug the cable and put it back in. Again, logging off solves the connectivity issues.

I have already tried with a new, pristine user account and the issue is still there.

Any ideas?

---

