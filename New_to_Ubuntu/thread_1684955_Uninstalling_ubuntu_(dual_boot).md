---
title: "Uninstalling ubuntu (dual boot)"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by joe1363 on 2011-02-09
Hello. I recently screwed something up on ubuntu and all I get is a black screen when starting up. It seems like reinstalling is my only choice now. Will removing ubuntu via the add/remove programs on windows completely remove all traces of ubuntu so that I'm ready for a fresh install? I don't have any important files on ubuntu, so I don't have to worry about backing up anything. Thanks

---

### Post by jonnny_j22 on 2011-02-09
hi there,

Probably best check you've not just messed up grub - try reinstalling it from the live cd.

If still no luck, or you just want a fresh instaLL,you don't need windows at all, just use the live cd - use the same partitions as before, just make sure you 'tick' them to be formatted. Windows can't read linux file systems, so you won't be able to do anything from there unless you've got something like disk internals installed.

remember the two most likely reasons it's not working are the configuration of grub, and the drivers being used, so if either of these seem like something you were trying before it failed.. be sure not to to do the same again

---

### Post by Mark Phelps on 2011-02-09
If you were running 10.10, a black screen is not that unusual.

Before you reinstall, try the following:
1) Press the SHIFT key during boot to get a GRUB menu
2) On the menu, select the top-most Recovery Mode
3) Once in there, when you get a selection list, choose the one to repair broken packages
4) When that is done, when you get a prompt, enter "startx"

If all goes well, you will get a desktop back.

Do a normal shutdown and you should be OK for a while.

---

### Post by joe1363 on 2011-02-09
I believe what I screwed up is xorg. I was misinformed about graphic drivers and uninstalled xorg and installed xorg-edgers (which even now, I still don't know what it is). Even after I reinstalled xorg I still get the black screen.

I'll give repairing the broken packets a try. If that doesn't work, can someone confirm if uninstalling ubuntu through the add/remove programs in windows will completely remove everything? It said so on ubuntu.com that you can do so when you dual boot, but I just want to check.

---

### Post by wep940 on 2011-02-09
Are you doing a true dual-boot, or did you install Ubuntu via wubi, which creates the file system, etc., as a Windows file, Ubuntu itself as a process?  If you did a wubi install, you are not truely dual booting.  Since Windows just thinks of a wubi install as a program within Windows, you can use add/remove programs to remove it and be sure to delete the file.  After that you are free to reinstall.
 
If you are not using wubi, there shouldn't be an option in Windows to delete Ubuntu.  In that case just back up anything you might need and reinstall.
 
Before you do any of that, though, we should really try to fix what is wrong.  So, do you ever get to the logon screen and then after that go to the blank screen?  Does Ubuntu appear to boot and then you have the blank screen?  Try holding down ctrnl-atl and press F1 - do you get a terminal log in screen?

---

### Post by joe1363 on 2011-02-09
Excuse my noobness, I didn't know there was a difference between a wubi install and a dual boot. I tried repairing the packets through recovery mode, but after I rebooted I got the same black screen. 

To elaborate, when I start my computer I get the option between windows and ubuntu, followed by the other ubuntu option (the grub screen I believe).  I get to see the ubuntu start up screen, but before I get the chance to log in I get a black screen. I still get to hear the login screen sound afterward though. It seems like ubuntu is running, but with a black screen.

I installed through wubi because the disc drive on this laptop is busted, so that rules out any cd based reinstalling. Thanks for confirming I can remove through windows. If I can avoid reinstalling that would be great though.

---

### Post by wep940 on 2011-02-10
When the screen goes black, and all the disk activity is done, and the login sound has played, what do you get when you hold down ctrl & alt and press F1?  If you get a text mode terminal screen, then log in with your normal userid/password (if needed, don't remember off the top of my head).  When you get to the command prompt, type:
 
lspci | grep VGA <press enter>
 
That *should* come back with a line that tells what video adapter you have.  If it doesn't, then type:
 
lspci <press enter>
 
Either way, post the output back here and we can try to get the driver installed.

---

