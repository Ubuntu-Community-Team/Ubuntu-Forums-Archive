---
title: "2 Questions, please help"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-10-12
I have 2 questions. My first question is, is it possible to make a ubuntu disk image?  I have made several disk images on windows using easeus todo backup, but of course that doesnt work on ubuntu.  Any solutions?

Also my next question is, right now i am dual booting windows 7 and ubuntu 10.10.  I would like to play around with some other bootloaders.  After i mess around with them, most likely i will want grub to be my bootloader again.  So how do i go about reinstalling grub as a boot loader to boot ubuntu and windows 7.  I know on windows its easy, you just run the windows recovery disk and it fixes everything.  Is there a simple way to to reinstall grub?

I am pretty new at ubuntu so if possible could you explain in detail. Thanks

Thank you for your help

---

### Post by slooksterpsv on 2010-10-12
Ubuntu Disk image, like with programs you've installed? Or do you mean like a recovery image where it has all your data as well? If either of those, look into installing: remastersys - it's an amazing program. All you do is install it, run it from System -> Administration -> remastersys and select the options like dist, backup, etc. 

With the backup portion you can edit a file to not include directories, or files e.g. so if I didn't want to include my downloads folder (60GB) on the image, I would edit the file and change the setting to "/home/<name>/Downloads" - where <name> is your username. - Don't have the program yet to give specifics, but I'll install it soon.

As for question 2, I would download and run VirtualBox, and install Ubuntu in a VM, and play with bootloaders that way, I love using GRUB and BURG together, makes Grub look beautiful, a lot of others have posted how to do this on the forums, use the search function.

---

### Post by AndyM3 on 2010-10-12
For system backup and restoring, I suggest you try Deja Dup (it's in the Software Center). If you want to mirror hard drives, you can probably use the Clonezilla Live CD.
Regarding your other question, I suggest you don't mess with bootloaders. GRUB is probably the best there is, and if you want something graphical look into BURG ([tutorial here]("http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/")).

---

### Post by hunter99507 on 2010-10-12
Thanks for the advice.  For reference for myself i would like to know how to reinstall grub. Any ideas?

---

### Post by Clever_Username on 2010-10-12
[link]("https://help.ubuntu.com/community/Grub2")

---

