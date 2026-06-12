---
title: "Installation problem"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by dankev on 2009-01-15
Hello. It may be that I'm missing something very simple, but I'm having trouble with my installation. After I boot the CD (8.10), I select "Install Ubuntu." It shows what looks like an installation screen for a couple minutes, then I get a text screen. There is some info there (I'll type it if anyone needs it), then:


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details

ubuntu@ubuntu: ~$ _



I don't know what to do here. Am I supposed to type in a command?

In case it is relevant, I'm using an Averatec 3200. It had XP, but I've been trying out Win 7. 

Thanks in advance for the help.

---

### Post by Temposs on 2009-01-15
Well, that appears to not be correct. I suspect something is crashing, if this happens when you select "Install Ubuntu"

What happens if you choose to try out Ubuntu using the Live CD? Does it boot into Ubuntu with that? You can also install from there.

---

### Post by jimmy the saint on 2009-01-15
It seems to be a known issue with that make/model.
there is a possible solution here:
[http://www.linuxcompatible.org/Averatec_3225HS_c12097.html](http://www.linuxcompatible.org/Averatec_3225HS_c12097.html)
but it may be more difficult than it is worth.
You may try to download the alternate cd
[http://mirror.its.uidaho.edu/pub/ubuntu-releases/8.10/](http://mirror.its.uidaho.edu/pub/ubuntu-releases/8.10/)
and select the appropriate alternate cd for you computer (either 32 or 64 bit)
It uses a text based installer (dont worry it is still menus and such, it is just keyboard arrow keys only and not as pretty).  It may do the trick.

---

### Post by dankev on 2009-01-16
> **jimmy the saint said:**
> 
You may try to download the alternate cd
[http://mirror.its.uidaho.edu/pub/ubuntu-releases/8.10/](http://mirror.its.uidaho.edu/pub/ubuntu-releases/8.10/)
and select the appropriate alternate cd for you computer (either 32 or 64 bit)
It uses a text based installer (dont worry it is still menus and such, it is just keyboard arrow keys only and not as pretty).  It may do the trick.
Cool. I'll try that. Thanks.

---

### Post by dankev on 2009-01-16
Ugh. I downloaded the alternate. This time it went all the way through the install process. I ejected the cd and rebooted. I entered my user name(comp2) and password. Then...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details

comp2@ubuntu: ~$ _


I'd try to do the thing in the first link from Jimmy, but I don't have a clue what it means. What's my next move?

---

### Post by jimmy the saint on 2009-01-16
Read this question at launchpad.  Essentially, this guy found the solution to your problem (I think).  He installed an older version (7.10 Gutsy Gibbon) and then upgraded that installation with apt-get.  It sounds more complex than it actually is.  Gutsy is available here:
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Upgrade the version to at least 8.04 (once).  That one is a long term release, so will be supported for three years as opposed to 18 months.

---

### Post by dankev on 2009-01-16
I'll try that and let you know how it goes. Thanks again.

---

### Post by dankev on 2009-01-16
OK, I've tried 2 older versions. 

When I tried 6.06, it wouldn't boot with the disc. It just tried to start in 8.10 with the same problem.

With 7.10, I get to the install screen, but when I select "install" (or any of the other options), I get:

I/O error
Error reading boot CD
Reboot 

Do I just need to try burning a new copy of 7.10, or downloading the 7.10 alternate, or downloading an earlier or later version? Or something else?

---

