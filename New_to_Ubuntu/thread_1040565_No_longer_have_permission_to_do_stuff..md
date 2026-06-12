---
title: "No longer have permission to do stuff."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-15
I used gksudo one time to install a font, and now I don't have permission to unmount a dvd, something I could do hassle-free before using this command.

What exactly just happened? I only use the command one time to install a font, and now I've lost permission to do certain stuff. (God-forbid I could log in as root ._.)

So, how can I get the permission to unmount the dvd permanently (as in, whenever I want), like I used to have?!

---

### Post by HermanAB on 2009-01-15
The font install and the DVD problem are probably unrelated.

DVDs (all removable media) are auto-mounted by HAL in the /media directory.  In there are two hidden files called .hal-mtab and .hal-mtab-lock.  You can force unmount the DVD, eject it and then delete these mtab files, then things should work like normal again when HAL recreates the mtab file next time you plug something in.  So try this:

Remove ALL removable media (USB drives, cameras, memory sticks, DVDs).
Let's assume the DVD is stuck and won't pop out:

$ ls /media
Everything you see are leftovers of things that are not there anymore.  /media should be empty when all removable schtuff is removed.  If the DVD is stuck, then you may see /media/disk or /media/cdrom or some such.

Do a lazy unmount of the stuck media and pop it out:
$ sudo service haldaemon stop
$ sudo umount -l /mnt/cdrom
$ sudo eject

Now see what is there and delete all leftover crud in /media:
$ sudo ls -al /media
$ sudo rm /media/.hal-mtab
$ sudo rm /media/.hal-mtab-lock
$ sudo rmdir /media/disk

and so on, till /media is clean.

Then restart HAL:
$ sudo service haldaemon start

Now, if you pop something in again, it should mount properly and do use the 'Safely remove' thing to keep things from screwing up again - don't just yank out a memory stick.

Cheers,

Herman

---

### Post by mattbutsko on 2009-01-15
Thanks for the instructions, I'll copy em down for future reference, but I just restarted X, something I should have troubleshooted and it works 90% of the time. If not, I just re-run gksudo nautilus and I can usually do whatever I need.

---

