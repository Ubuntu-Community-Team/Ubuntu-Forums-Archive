---
title: "TuxonIce uswsusp Suspend2... Confused"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by toothdecay on 2009-01-24
Forgive me, but I'm confused ;)

Are these all different solutions to the same problem? What is the difference between TuxonIce and the system Ubuntu uses or am I confused about the whole concept.

I guess I'm really curious to why suspend/hibernate seem like such an issue for so many people (including myslef)

:D

---

### Post by kerry_s on 2009-01-24
there just different programs that do the same thing.
i prefer uswsusp myself, it's always been the fastest for me.

your on a vaio? on my vaio i used "sudo s2ram -f" to suspend and "sudo s2disk" for hibernate and "sudo s2both --force" to suspend with a hibernate backup.

---

### Post by toothdecay on 2009-01-24
Yes, I had no luck with s2disk and s2both, and I'm not even sure what happend to s2ram, it doesn't even exist in the latest package.

The only luck I've had is with suspend by forcing sleep.sh with a few tweaks to the acip-support fle. 

I don't REALLY understand why it works though, all I know is that its damned slow and I have to sit with my latop until it goes to sleep, which is a weird thing to have to do with a peice of technology. :rolleyes:

---

### Post by kerry_s on 2009-01-24
yeah, a lot of the main distro's use pm-utils, which works but is dog slow, you might as well shut it down, it would be faster. :lolflag:

i heard about the missing s2ram before, can't believe they didn't fix that yet.

---

