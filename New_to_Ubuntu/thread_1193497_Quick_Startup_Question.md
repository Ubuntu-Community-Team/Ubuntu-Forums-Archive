---
title: "Quick Startup Question"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Dr Belka on 2009-06-21
You know that screen, during startup.  It is the one after GRUB and it has the ubuntu logo with the loading bar across the bottom.  Since I did a "aptitude safe-upgrade" and installed a new kernel, that screen no longer shows up and now it just says "reading files needed to boot" and then displays many lines of text as it boots up.  While this doesn't bother me too much, I would rather hide all of the text and just have the loading screen.  How do I turn that back on?

---

### Post by zzHanks on 2009-06-21
Try: Press 'C' or 'E' (don't remember, you should see it) in GRUB and add 'splash' instead of 'quiet' (if it is) in the end of the line.

---

