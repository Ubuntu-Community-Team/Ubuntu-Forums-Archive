---
title: "want to go 9.04 to 8.04"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by flyingsolo on 2011-01-08
My old dell inspiron 6400 ran fine under 8.04 but when I attempted to go to 9.04, I can only work in command line interface b/c I think the graphics card is no longer supported (I can't remember the details).  However, I did boot from an old kernel in the bootscreen list and got back to 8.04 so I can use the laptop again.
I'd like to remove the newer OS so that the laptop will only load 8.04 and no longer go into 9.04.  At least i can still use it for some basic work though it's looking more & more like an antique!  I need someone's advice on how to proceed to 'downgrade' back to the last useable version of U for this device.
Thanks

---

### Post by oldos2er on 2011-01-08
There is no downgrade possible that I'm aware of; you'd need to reinstall 8.04 (which will reach its end-of-life this April).

What video card do you have?

---

### Post by flyingsolo on 2011-01-08
It is: ATI Radeon Mobility X1400
if I'm reading the lspci correctly.  I vaguely remember there being issues with X support or something along those lines.

---

### Post by rondackcpu on 2011-01-08
If I understand you correctly, you are in a "dual boot" situation which allows the selection of either of two installations at grub time.  If that is the case, there is no need to reinstall anything.

You might try this first:  Get 8.04 running by selecting from grubs menu.  Then reinstall grub.  This should put 8.04 at the head of the boot list as it was before.

If that doesn't work, you might try this: That old "grub" has an easy to edit file which lists the order in which the operating systems can be selected.  I think it is called "/boot/grub/grub.conf" or a name nearly like that.  It will be located in the ROOT file of the most recently installed operating system.  Edit it to put an entry for 8.04 at the head of the list.

If I am sending you astray, someone else please help.

Sorry, forgot other thought -- the ATI X1600 card should work just fine with either of those editions of Ubuntu.  I have an ATI X1800 running OK.  Maybe there is some other problem that might be fixed before you go back to 8.04.



CRS

---

### Post by oldos2er on 2011-01-08
I found this thread: [http://ubuntuforums.org/showthread.php?t=1468484](http://ubuntuforums.org/showthread.php?t=1468484)
Just glanced through it so I'm sure what's there, but it looks as though ATI dropped support for that card, at least on Linux.

---

