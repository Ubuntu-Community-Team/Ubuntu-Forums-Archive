---
title: "grub rescue from hibernation"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by djthebogan on 2010-07-28
Hey everyone, i'm new to linux and have just started using it.  i have been using it fine until i went into hibernation and now it just goes to a screen saying grub rescue.  Is there any command or anything i can do from here to just boot up?  I have tried searching for an answer but haven't found anything really that helps. So does this mean that i can never use hibernation?  thanks

---

### Post by quixote on 2010-07-31
If you shutdown (eg by pushing the power-off for 5 secs) and then restart, will it boot?  I.e. is this just a problem after hibernation?  Is it also after suspend?  If it won't boot at all, then, as it says in the Hitchhiker's Guide: don't panic.  It's a bit tedious, but it's actually straightforward to recover grub if you need to.  Your data are fine and nothing's been damaged. If this is the problem, I'll give you the grub steps to go through.

If you can boot from shutdown, just not after hibernate, then the simplest thing is probably not to use hibernate, unless you really want to troubleshoot the issue.

---

