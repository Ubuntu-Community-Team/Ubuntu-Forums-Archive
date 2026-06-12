---
title: "Problem adding ubuntu at Boot Loader"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Achmo on 2011-03-26
Hello all..I am a newbie at using ubuntu and i have a problem...Ok here it goes: i used wubi trought windows 7 to install ubuntu 10.10(in a different hard disk) and everything was ok..but i had to format windows 7 and reinstall it, and after that i lost the option to log in at ubuntu at windows boot loader..i tried selecting the hard disk of the ubuntu and log in but i had an error message(something about ntfl/s not sure but i can recheck if u want).. The thing is a tried adding ubuntu with easyBCD but i failed,and all guides are about a new installation of ubuntu.. I dont want to format ubuntu too so , is there a way to add it at boot loader again? And also,when i used wubi there was a selection to up to 30giga of free space...Can i increase the free space? Thanks, and sorry for any mistakes

---

### Post by goldaryn on 2011-03-26
<edit>

---

### Post by fabricator4 on 2011-03-26
> **Achmo said:**
> also,when i used wubi there was a selection to up to 30giga of free space...Can i increase the free space?

The "free space" is the amount of extra space allocated to the virtual drive at the time you do a Wubi install.

A Wubi install is done inside Windows, it is not installed on a separate drive or partition.  For this reason I believe you did a Wubi install, not a full install of Ubuntu on the other device or partition.

If that is the case, when you re-installed Windows, your Wubi install would have been overwritten, since it only existed as a program installed in Windows.  This is why when you try to boot off the second device you get an error - Ubuntu is not installed there.

Even if Ubuntu was installed on a separate drive or partition, installing windows again will overwrite your grub on the first device.  It's possible to reinstall grub off the LiveCD with the grub-install command (eg "sudo grub-install /dev/sda") however I still believe this was a Wubi install - grub is not going to find any Ubuntu install.

Now that you've got Windows booting OK, you can do a proper dual boot install of Ubuntu if you want.  I suggest you have a read of the Ubuntu community documentation regarding doing a [dual boot install]("https://help.ubuntu.com/community/WindowsDualBoot") and ask further questions before going ahead if there's something you don't understand.

I'd recommend release 10.04 as the most suitable release if you're new to Ubuntu.  The latest release 10.10 may present some extra challenges such as a problem (bug) with the installer if you select the "dual boot" mode.  The only exception to this advice would be if there is hardware support in 10.10 that does not exist in 10.04.

Chris.

---

