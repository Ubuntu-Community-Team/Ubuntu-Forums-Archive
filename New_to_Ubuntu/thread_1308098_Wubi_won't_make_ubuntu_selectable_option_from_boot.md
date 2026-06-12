---
title: "Wubi won't make ubuntu selectable option from bootloader (Win 7)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Dullstar on 2009-10-31
Maybe the 9.10 version works better, but I can't get Wubi to let me boot into Ubuntu (for several reasons, I want the LTS, not 9.10).
I am using Windows 7.

---

### Post by Dullstar on 2009-10-31
bump

This is urgent!

---

### Post by sandyd on 2009-10-31
perhaps wubi is currently not compatable (yet!) with windows 7.

---

### Post by Dullstar on 2009-10-31
That could be it.  Has anyone managed to get an actual install of 8.04 to work in a dual boot with Win 7 (unlike 9.10's bootloader with WinXP) with little or no tweaking?

Also, other distributions count as well, you can mention them.  Preferably they should fit on a CD (and please no really lightweight ones that are more meant for slow computers, do not care on DE, but do prefer GNOME over XFCE and XFCE over KDE.  Oh, wait, and I really hate LXDE.  Don't argue, just accept.  And it's no big problem with KDE - I did see a picture of Gentoo that appeared to use KDE on Wikipedia that looked really good.

---

### Post by dzon65 on 2009-10-31
Check out youtube [http://www.youtube.com/watch?v=m5Jxfj6tu_U](http://www.youtube.com/watch?v=m5Jxfj6tu_U)
And google for dualboot ubuntu 9.10 in win7

---

### Post by Dullstar on 2009-10-31
Nice, but I was kinda looking for 8.04 information...

---

### Post by Dullstar on 2009-11-01
bump

---

### Post by Dullstar on 2009-11-01
I'm giving up here, and just installing 9.10.  At this point, I just want my linux back!

---

### Post by planetbeing on 2009-11-02
8.04 should work fine with Wubi in Windows 7, I believe with no tweaking. What exact steps did you do and what went wrong?

I recently migrated an existing Hardy Heron Wubi installation from Windows XP to Windows 7, so I can give you instructions on doing that if you want. I don't have any experience with doing a fresh install of 8.04 on top of Windows 7 but I imagine there shouldn't be any problems.

EDIT: Here's the instructions for the migration just in case someone stumbles on this and wants them.

The general goal is to reproduce exactly what the Wubi installer would have done for Windows 7 (without it going through and making a fresh Ubuntu disk image and install... the disk image is independent of the Windows versions). I assume Ubuntu was installed in C:\ubuntu in the old OS. These same instructions will work if the target system is Vista as well.

1. Copy C:\ubuntu to C:\ubuntu from the old system to the new system.
2. Copy the two files C:\ubuntu\winboot\wubildr and C:\ubuntu\winboot\wubildr.mbr to C:\
3. Go to Start and type in cmd. Right-click cmd.exe and click Run as Administrator.
4. In the cmd window, issue the command: bcdedit /create /d "Ubuntu" /application bootsector
5. Note down the UUID identifier the command returns. Mine is {773d31e4-c3bd-11de-83ed-b036f4cbaf34} but yours will be different. You will need this identifier for the next steps.
6. Enter the command: bcdedit /set {your-identifier} device partition=C:
7. Enter the command: bcdedit /set {your-identifier} path \ubuntu\winboot\wubildr.mbr
8. Enter the command: bcdedit /displayorder {your-identifier} /addlast
9. Enter the command: bcdedit /timeout 10
10. Enter the command: fsutil fsinfo ntfsinfo C:

Note down what it says for "NTFS Volume Serial Number". Take what is after the 0x and capitalize any letters in the serial number. You should end up with something that's 16 characters long with numbers and capital letters.

11. Open C:\ubuntu\disks\boot\grub\menu.lst with a text editor that can handle UNIX newlines (like Notepad2: [www.flos-freeware.ch/notepad2.html](www.flos-freeware.ch/notepad2.html)). This is your new partition UUID

12. Replace all instances of root=UUID=XXXXXXXXXXXXXXXX (where XXXXXXXXXXXXXXXX is your old partition's UUID) with the new partition UUID.

That's it. Reboot and you'll be able to select Ubuntu from the boot menu.

You can also replace C: with any other local drive letter if you put the Wubi files elsewhere. Steps 10-12 are just the extra steps for migration.

---

### Post by Dullstar on 2009-11-02
I did run Wubi 9.10, so let's see if it worked. ](*,)

---

### Post by Dullstar on 2009-11-06
I'm marking as solved due to a successful, working 9.04 install from a LiveCD.  And it didn't hose the computer (I checked, Windows XP (Windows 7 broke, but that's alright, it sucked anyways) still boots, or it should, as I only let it get to the ugly Win XP screen and then powered off to go into my new 9.04 installation.

---

