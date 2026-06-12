---
title: "Suspend &amp; hibernate"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by ozbolt on 2010-05-06
I have an HP notebook that works just great but Ubuntu doesn't do everything as it should. One problem is with Suspend and resume. What happens is it doesn't wake up and I have to restart it all. While Win7 does that flawlessly.
There is very good information about my computer:
[http://dl.dropbox.com/u/520845/hardinfo_report.html](http://dl.dropbox.com/u/520845/hardinfo_report.html)

What line in what conf file do I have to edit?
Which thread from this forum do I have to check out?

Thanks for help

---

### Post by jbrown96 on 2010-05-06
It's probably your graphics card driver. Did you install fglrx? Check in System-->Administration-->Hardware Drivers.

---

### Post by derande on 2010-05-06
what is your swap partition size? it may be too small.

---

### Post by jbrown96 on 2010-05-06
> **derande said:**
> what is your swap partition size? it may be too small.
Swap is not needed for suspend (sleep), just for hibernate.

---

### Post by ozbolt on 2010-05-09
The Swap size is 12G. Probably enough :)
While after installing ATI own driver (through Hardware Drivers) both suspend and hibernate still doesn't seem to work.

Any log you could use?

---

### Post by anewguy on 2010-05-09
Okay, first off I've never done this, but......

Going by run-type (someone more knowledgeable than me currently would have to tell you which it would be on wake from suspend or hibernate), you should be able to add things to the rc file structures to:

(1) do a gdm restart (or startx, maybe both)

(2) restart the wireless if needed


I am currently not sure of the syntax, but thought I'd throw these out there for someone with more knowledge to expound on.  I read a thread about restarting video on wake, but wasn't able to find it again.  I know it went in one of the rc.x files but just don't remember it.  Restarting wireless should be the same sort of thing.

Dave ;)

---

### Post by anewguy on 2010-05-09
Found some of the things I was thinking about, but still need to search for more of them.  A little out of date, as I think some of this is now included with Ubuntu, but tools to look at none the less:


[http://en.opensuse.org/S2ram]("http://en.opensuse.org/S2ram")

[https://wiki.kubuntu.org/DebuggingKernelSuspend]("https://wiki.kubuntu.org/DebuggingKernelSuspend")

[http://ubuntuforums.org/showthread.php?t=750216]("http://ubuntuforums.org/showthread.php?t=750216")

[http://evanjones.ca/ubuntu-tips.html]("http://evanjones.ca/ubuntu-tips.html")

From what I've been reading (e.g., none of this was my knowledge - just passing it along), you should also try:

- when trying to wake from hibernate or suspend, try toggling the caps lock key and see if the caps lock light toggles on/off with the button.  If so, it is most likely a video restart problem.  If not, it is most probably a BIOS and ACPI problem (which can be adjusted with sv2ram, as mentioned in 1 of the above posts and apparently included now with Ubuntu).

- if the toggling of the caps lock key/caps lock light works, try restarting X by holding down the ctrl and alt key and pressing the backspace key.

I'll keep checking for more of what I was thinking of, but wanted to pass this on to you now.  Let me know how the caps lock key/light goes when waking.

Dave ;)

---

### Post by anewguy on 2010-05-09
Found another thing to check/try - in particular, look for the first post by user "Benlog":

[http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html]("http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html")

Please note I haven't tried any of the things I have posted here to you, as I don't use that functionality.  So, if you don't understand something or are leary of using it, just post back and we'll see if we can get somebody with more experience in that area to help out as well.

Dave ;)

---

