---
title: "Grub Error 17 and Installation Issue"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by bizghetto2 on 2009-04-28
Ok so I have a Dell computer that is at least 4 yrs old. It crashed last summer and I got angry at windows and decided I would try linux and a friend gave me the Ubuntu 8.04. This past Sunday the update manager started to act funny (as in it kept failing to update) I decided to restart the computer and while its rebooting it keeps saying Loading Grub and then error 17... after that it just stays like that with the underscore blinking. I said screw it and I would just reinstall linux. I booted from the CD (somehow after messing w/ BIOS) and now whenever I try to pick which partition to format.. it says "no root chosen" or something like that. I read from a forum site doing a google search that I should make a new partition,

1. being ext3 with a /  as the something point
2. the second being swap...

this takes me farther then any other way I've tried but when it gets to actually formating the partition it gets to 15% and then says failed.

I'm literally typing this only by running off the CD itself... and as you can tell I'm like a linux 2 yr old so any response unfortunately has to be rather explicit. PLease help!! I really was thinking that if I couldn't get it fixed I'd get a new computer or be cheap and buy an external hard-drive for the time being and save things on that.

ANY help is highly appreciated and any information I'm missing I'll be more then happy to supply.

---

### Post by MontelEdwards on 2009-04-28
> **bizghetto2 said:**
> Ok so I have a Dell computer that is at least 4 yrs old. It crashed last summer and I got angry at windows and decided I would try linux and a friend gave me the Ubuntu 8.04. This past Sunday the update manager started to act funny (as in it kept failing to update) I decided to restart the computer and while its rebooting it keeps saying Loading Grub and then error 17... after that it just stays like that with the underscore blinking. I said screw it and I would just reinstall linux. I booted from the CD (somehow after messing w/ BIOS) and now whenever I try to pick which partition to format.. it says "no root chosen" or something like that. I read from a forum site doing a google search that I should make a new partition,

1. being ext3 with a /  as the something point
2. the second being swap...

this takes me farther then any other way I've tried but when it gets to actually formating the partition it gets to 15% and then says failed.

I'm literally typing this only by running off the CD itself... and as you can tell I'm like a linux 2 yr old so any response unfortunately has to be rather explicit. PLease help!! I really was thinking that if I couldn't get it fixed I'd get a new computer or be cheap and buy an external hard-drive for the time being and save things on that.

ANY help is highly appreciated and any information I'm missing I'll be more then happy to supply.
Well you being so new to Linux and stuff, why don't you just use the "Use whole disk" or something like that. It basically dose the same thing, and I believe that it makes it ext3. And if nothing else helps, use the Alternative Installer, i never use the Live CD, well i will from USB but not from the CD

---

### Post by Miljet on 2009-04-28
From the symptoms you describe, it really sounds to me that your hard drive is toast. While using the live CD, see if you can mount the drive and copy any data from it.

Then again, it might just be that the partition table has become corrupted. In that case, a re-format and install should fix the problem.

---

### Post by bizghetto2 on 2009-05-01
I have tried to install using the whole disk feature but it still gives me a failed notice. I never thought to download a different version onto a usb drive and try it from there. I'll see what happens if I maybe try a different version of linux.

---

### Post by halitech on 2009-05-01
you may want to test the disk by downloading (obviously on another computer) the UBCD and testing the drive with the tools on it

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

