---
title: "Jaunty: stop startup remembering apps"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Nicodemus144 on 2009-05-17
hey there.

so i decided to experiment with startup remembering the apps i was running last time.  i no longer want to use this feature and have unchecked the "Automatically remember" box under System->Preferences->Startup Apps, but it continues to start with the same apps automatically running (firefox and tomboy.)

any idea how to make this stop?  thanks!

---

### Post by Joeb454 on 2009-05-17
If you check under the same menu, are firefox and tomboy still in the list to be automatically started?

Sounds simple, but it's one of those things that's easy to overlook/overthink ;)

---

### Post by Nicodemus144 on 2009-05-17
understandable.  first thing i checked.  they are not.

---

### Post by Mempho on 2009-05-17
Recheck "Automatically remember", close all running apps, and reboot. Then uncheck "Automatically remember" and reboot again. No apps should start. Simply unchecking "A...R" will not clear out the programs it's remembering. You have to manually clear the memory, reboot, then uncheck "A...R". This confusing "feature" allows you to setup a desktop, then uncheck "A...R" and have the machine always return to that base configuration you selected, while ignoring any other programs you might have running at shutdown.

---

### Post by Nicodemus144 on 2009-05-18
thanks Mempho!  that did it! =)

---

