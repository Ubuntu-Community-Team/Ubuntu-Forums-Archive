---
title: "soundcard issue new update"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by navidson on 2009-01-11
after updating my ubuntu 8.04 my sound no longer works in one of the threads someone suggested using the old kernel which is aparently 2.6.24-22-generic kernel. in startup i pressed esc. and that option wasn't there. only the recent one. 2.6.24-23 and -16 was there. not the 2.6.24-22-generic kernel. i would love to have some sound and i'm pretty lost is there a way to get 2.6.24-22-generic kernel or what should i do so my sound works again...it worked when i first installed ubuntu off the disk i got with my laptop. i have a dell 1525 inspiron just got it a few months ago with linux installed on it.  this is my sound card.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

any help would be appreciated..i'm not super computer smart so thanks.

---

### Post by jemate18 on 2009-01-11
> **navidson said:**
> after updating my ubuntu 8.04 my sound no longer works in one of the threads someone suggested using the old kernel which is aparently 2.6.24-22-generic kernel. in startup i pressed esc. and that option wasn't there. only the recent one. 2.6.24-23 and -16 was there. not the 2.6.24-22-generic kernel. i would love to have some sound and i'm pretty lost is there a way to get 2.6.24-22-generic kernel or what should i do so my sound works again...it worked when i first installed ubuntu off the disk i got with my laptop. i have a dell 1525 inspiron just got it a few months ago with linux installed on it.  this is my sound card.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

any help would be appreciated..i'm not super computer smart so thanks.


do you still have the old kernel? Did you used update to have your kernel updated?

To check if you still have the old kernel.

Try this,

1. Applications -> Accessories -> Terminal
2. $ cd /usr/src
3. $ ls

if there are entries matching your old kernel, it is still there you just have to edit grub. For example, your old kernel is 2.6.27-9

Then the entry listed after the ls command is linux-headers-2.6.27-9

---

### Post by navidson on 2009-01-11
this is what came up does it matter what kernel it is?

ryan@dell-desktop:/usr/src$ ls
linux-headers-2.6.24-16          linux-headers-2.6.24-23
linux-headers-2.6.24-16-generic  linux-headers-2.6.24-23-generic

those are the options that came up in my bios when i pressed esc in startup...should i just choose the 2.6.24-16-generic or is there a better option and will it start up like that everytime?

---

