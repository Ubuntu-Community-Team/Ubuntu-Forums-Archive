---
title: "mouse &amp; keyboard freeze-up on Dell Vostro 1310"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by al.adab on 2009-11-14
Hello,

mouse and keyboard occasionally didn't respond on my Dell Vostro 1310 - OS: Ubuntu 9.04. I fixed it according to
[http://ubuntuforums.org/showthread.php?t=1164008](http://ubuntuforums.org/showthread.php?t=1164008)

I've just installed Ubuntu 9.10, and I wonder if there's a similar solution, should the bug present itself again - well, the mouse already froze twice at start-up...

/boot/grub/menu.lst appears empty (unlike on 9.04), by the way. Is there any other file I should be editing instead? 

Thanks.

---

### Post by jnorthr on 2009-11-14
is the mouse built into the dell or can you replace it or try someone else's mouse just for a test? it may be easier to buy a new mouse than worry with your current one.

---

### Post by al.adab on 2009-11-14
Tested it with an external mouse a few times. The in-built pad mouse froze once, I plugged in the external mouse and that worked (the in-built one still didn't respond), but the keyboard didn't respond. It only happened one out of five re-boots, and if it weren't just the mouse I'd be ok, but if the keyboard freezes that's really annoying...

---

### Post by al.adab on 2009-11-16
...any idea?

---

### Post by al.adab on 2009-11-18
>>bump<< 
:)

---

### Post by al.adab on 2009-11-18
...now, I've been blind experimenting...:) 

ref: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

a) I typed GRUB on Terminal. Was told that GRUB is not installed. I installed it + rebooted. Nothing seemed to have changed. 

b) as */boot/grub/grub.cfg* cannot be edited, I copied and pasted its content (from *### BEGIN /etc/grub.d/00_header ###*) onto */etc/grub.d/40_custom*

c) I edited */etc/grub.d/40_custom* by inserting the line *i8042.reset* after each *quiet splash* in the file (two entries). I also added the word *quiet* at the end of each of these two entries. This is what I previously did on Grub in Ubuntu 9.04. 

d) I've been re-booting a few times. The mouse and/or keyboard haven't so far frozen, but it might...

Question 1: Is the experiment sloppy or have I by miracle made sense (without knowing what I'm doing?)? 

Question 2: I can't understand the new Grub theory (and probably wouldn't even if you explained to me). In any case, shall I keep the Grub I installed or am I better off if I remove it? 

Thanks.

---

### Post by ukripper on 2009-11-18
> **al.adab said:**
> 
Question 1: Is the experiment sloppy or have I by miracle made sense (without knowing what I'm doing?)? 

Question 2: I can't understand the new Grub theory (and probably wouldn't even if you explained to me). In any case, shall I keep the Grub I installed or am I better off if I remove it? 

Thanks.

GRUB2 is already there as default with 9.10. don't know what exactly you installed. Your experiment is actually correct way how Grub2 should be edited.** Do not** edit /boot/grub/grub.cfg.
After you have made changes to 40_custom, you need to run below command:

```
sudo update-grub
```

This will persist your changes even if new kernel is updated.

---

