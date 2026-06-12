---
title: "Want to dual boot windows 7"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-09
Ubuntupals:

I am currently running 32 bit Windows 7 on an inexpensive new Acer computer. My son plays Guild Wars, which, sadly, does not run too well under Wine, but that is another story. So I had to wipe my beautiful 64 bit Karmic install off to put Windows 7 on. Now, I'd like to put 64 bit Karmic back on. So, if I install, repartition, and run grub-update in a terminal, will that do it? Or, does Windows 7 not play well with others?

---

### Post by RedSingularity on 2009-11-09
When you run the karmic install it will give you an option to install alongside winblows.  Then when you boot you can select winblows or linux through the GRUB.  You dont need to mess with grub if you have winblows installed first.  The disk will do everything for you.

---

### Post by dndrich on 2009-11-09
Wow!  That was a quick response.  OK, I'll give it a try.

---

### Post by ranch hand on 2009-11-09
You may need to run update-grub after installation to get Win JerryLewis Pro on the menu.  It happens that it is missed by the installation running update-grub (which it does).

You should not have a problem.  Stick with ext4.  That way you can read MS files but it won't work the other way.  Good security thought when you have a security hole installed on your box.

---

### Post by dndrich on 2009-11-09
OK, sounds good. Fortunately, this computer is not mission critical at my house. I bought it as a test platform. Just so happens my kid loves Guild Wars on this computer, which just performs better under Windows Jerry Lewis. But, he gets some occasional crashes with his school work. I was running Karmic on that computer, and it was really solid.

---

### Post by ranch hand on 2009-11-10
There, in a nutshell, is why it took me 3 days and my wife 3 weeks to decide we needed Vista off this new box.

I like to think of those nice folks from MS as friends.  If it wasn't for them I would still use their products.  This is more fun.

Besides, I bet if I had all 4 cpus cranked to 100% running Win JerryLewis Pro I would have some problems (I run boinc with World Community Grid work units).  I am on my "night" OS now Stoner Edition1.0, a 9.04 respin, and it has worked this way since May.  My day OS is an upgraded 9.04>9.10>10.04testing OS running a boinc alpha test release.  100% cpu, solid as a rock for all normal usage.

FUN

---

### Post by Mark Phelps on 2009-11-10
> **dndrich said:**
> Ubuntupals:... So, if I install, repartition, and run grub-update in a terminal, will that do it? Or, does Windows 7 not play well with others?

First thing you should do is use the Windows 7 builtin function for creating and burning a Seven Recovery CD.  That will come in useful later if you have to do a Startup Repair if the Ubuntu installer, in shrinking your Windows 7 partition, ends up corrupting it.

---

### Post by dndrich on 2009-11-10
That is good advice. But, this is a play computer really, so if I toast my 7 installation I will just reinstall it. But the recovery CD should make that quicker...I'll play with that.

---

### Post by dndrich on 2009-11-10
OK, did the install of Karmic 64 bit, and no problems at all. Grub2 recognized Windows 7. When launching Windows 7 it did a disk check after it had its partition resized, and all was well. Truly terrific. I now have my Ubuntu back. Now, when I try to mount my Windows 7 partition from within ubuntu, it won't mount because it wants to authenticate with a password. There is no password for that partition. Any thoughts on this? Not critical, but would be interesting.

---

### Post by ranch hand on 2009-11-10
Just type your password for 9.10.

If someone else is using your 9.10 do you want them to have easy access to your Win JerryLewis Pro files?  I bet not.

---

### Post by dndrich on 2009-11-10
Ah, I'll try that. I have no problem with access to the Windows Jerry Lewis files, because this is a play computer with nothing important on it. Windows is used for gaming only.

---

### Post by dndrich on 2009-11-10
OK, that worked. How stupid am I. Thanks for the info!

---

