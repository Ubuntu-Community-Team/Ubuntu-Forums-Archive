---
title: "Complete System Freezing"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by PyroSharpie on 2010-09-28
Okay, so I really don't have much experience troubleshooting problems on Ubuntu, other than my tried-and-true method of Googling, and that has failed me this time, so here we go..

My system:
Ubuntu 10.04 x64
AMD Athlon II X4
Radeon HD 4850

At seemingly random intervals, my whole system freezes.

At first i found it frozen whenever i came back after the computer was asleep for more than an hour or two. i would come back wiggle the mouse (as the system had by this time turned off the monitor) and the monitor would say that there was no signal, however the computer was still on and required a restart to work again.

I disabled the screensaver and told the computer not to turn of my monitor. After a few hours i would come back to a frozen desktop image on my screen and a nonworking mouse and keyboard.

It has since then frozen once while i was somewhat using the computer. i was watching a video in totem movie player and everything froze as it did before. sometimes the computer will not freeze for a whole day, and other times it will freeze several times throughout it.

I was also initially having an issue installing fglrx, and thought it *might* have something to do with that (even though i didn't think that that would explain the non-responsive keyboard...). I found a fix involving upgrading to the 2.6.32-25 kernel and swapping out this compat.h file, however the freezing problem did not stop.

i have done my best to search, but have found nothing to help me, and i just don't know how to go and troubleshoot this myself.

---

### Post by Rubi1200 on 2010-09-28
I just spotted this thread by another user and thought it might be worth taking a look at it:
[http://ubuntuforums.org/showthread.php?t=1584050](http://ubuntuforums.org/showthread.php?t=1584050)

This might also be the source of the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

Hope this helps.

Oh, and welcome to the forums :-)

---

### Post by PyroSharpie on 2010-09-28
> **Rubi1200 said:**
> I just spotted this thread by another user and thought it might be worth taking a look at it:
[http://ubuntuforums.org/showthread.php?t=1584050](http://ubuntuforums.org/showthread.php?t=1584050)

This might also be the source of the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

Hope this helps.

Oh, and welcome to the forums :-)
Hi, and thanks for the help and the welcome!
checking out the second link, it soulds quite familar, but as far as i can tell, i cannot use the (R-E-I-S-U-B) command to restart after a freeze as even the keyboard is locked up.

From the first link, there is no "Clocksource tsc unstable" entries in my logfile, but i dont exactly know how to check the overheating/memory/hard drive issues. I do however have Windows 7 install on here as well and i have never had any issues with it as far as the above mentioned things.

the "4. Kernel Crashing / Software issue - Read your logs (/var/log/messages) for clues." could be my problem i suppose, but i don't exactly know what to look for in the logs.

the main common entry occurring last before my restart time entries is like 5 or more entries of:
"usb 1-6.1: reset high speed USB device using ehci_hcd and address 6"
and sometimes a:
"gnome-screensav[2212]: segfault at 4 ip 00007fb3e500a38e sp 00007fffe8594ed0 error 4 in libGL.so.1.2[7fb3e4faf000+ae000]"

---

### Post by Rubi1200 on 2010-09-28
This > segfault needs investigating more because it is often a sign of something (a program, for example) accessing memory incorrectly or in a way that is not allowed.

Have you tried disabling the Gnome screensaver?

Might be worthwhile starting there.

Also, I would run memtest either from a LiveCD or the GRUB menu.

---

### Post by PyroSharpie on 2010-09-28
> **Rubi1200 said:**
> This  needs investigating more because it is often a sign of something (a program, for example) accessing memory incorrectly or in a way that is not allowed.

Have you tried disabling the Gnome screensaver?

Might be worthwhile starting there.

Also, I would run memtest either from a LiveCD or the GRUB menu.

Thanks for the help, i just ran a memtest from the GRUB menu, and it returned 0 errors

Also, the screensaver was disabled for some of the time, when i had disabled it from turning off my monitor earlier, i also disabled the screensaver as well at that time, but the freezes still happened then.

i have disabled it again though.

also small note that i have now updated in my original post, its a quad core not a dual core processor, if that makes a difference (i don't think it will but i'm playing it safe here)

---

### Post by PyroSharpie on 2010-09-29
BUMP back to first page.

Are there any other ideas i can try to fix this?

I tried reinstalling 10.04 and the problem still remained after a complete wipe and reinstall.

Do you think it would be a good idea for me to try the 10.10 beta?
or even switch to 9.10 and see if i have better luck?

---

### Post by Rubi1200 on 2010-09-29
> **PyroSharpie said:**
> BUMP back to first page.

Are there any other ideas i can try to fix this?

I tried reinstalling 10.04 and the problem still remained after a complete wipe and reinstall.

Do you think it would be a good idea for me to try the 10.10 beta?
or even switch to 9.10 and see if i have better luck?
I don't have any other ideas right now; sorry.

Try either 10.10 or 9.10 and see if the problems persist.

Good luck!

---

