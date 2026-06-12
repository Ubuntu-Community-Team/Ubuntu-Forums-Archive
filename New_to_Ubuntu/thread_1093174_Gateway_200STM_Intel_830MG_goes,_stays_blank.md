---
title: "Gateway 200STM/ Intel 830MG goes, stays blank"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by salmonsm on 2009-03-11
I have Xubuntu newly installed on a Gateway 200STM laptop. It has the Intel 830MG video chipset. Problem is, if the system is idle a while, the screen goes blank. I try to revive it and only get the pointer. you can tell the system is awake as as you move the pointer around it changes depending on what it might be pointing to, I just can't see anything on the desktop. the only way out is to reboot.

I've seen reports of this problem with various solutions suggested. I've tried all that I have seen, including disabling compiz (not installed), adding this line to the "Device" section of /etc/X11/xorg.conf:


Option "VBERestore" "yes"

changing the power management to disabled (setting hdparm to 254 or 255) and setting machine to never go to sleep under no circumstances in Applications--> Settings--> Settings Manager. Nothing has worked, HOWEVER, one one boot, after i had set the value in xorg.conf above and just manually set the hdparm and went to bed, when I woke up I COULD get the desktop back! I was elated. I went to make some coffee and when I came back, the old problem came back too. :(

This is a drag! I want to use ubuntu to run a media server and to manage playlists from my old iTunes Library, so a blank desktop after a period of inactivity is kindof a problem..

Has anyone solved this problem? Can I provide the output of something for someone to peruse?

Thanks.
Michael

---

### Post by Peter09 on 2009-03-11
Make sure that there is no screen saver enabled.

---

### Post by salmonsm on 2009-03-11
> **Peter09 said:**
> Make sure that there is no screen saver enabled.

I will, thanks.

Seems weird that the pointer would be functioning normally during blank-outs. But I will d-check.

---

### Post by skymera on 2009-03-11
What about if you go to a TTY then back to GUI?

When the cursor  only shows press 
```
 CTRL + ALT + F1  
```

Then to get back to GUI press

```
 CTRL + ALT + F7 
```

---

### Post by salmonsm on 2009-03-11
> **skymera said:**
> What about if you go to a TTY then back to GUI?

When the cursor  only shows press 
```
 CTRL + ALT + F1  
```

Then to get back to GUI press

```
 CTRL + ALT + F7 
```

Groovy, didn't know about this. Thanks, I will try.

---

### Post by skymera on 2009-03-11
I use the TTY when i;m compiling random bits.

Keeps it out the way and stops me from being able to just close it ^^

---

### Post by salmonsm on 2009-03-11
switching between tty and gui DOES bring the desktop back. Works for me. Thanks!

---

### Post by salmonsm on 2009-03-12
double post.

---

