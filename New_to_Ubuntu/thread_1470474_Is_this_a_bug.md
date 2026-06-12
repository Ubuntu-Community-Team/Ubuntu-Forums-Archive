---
title: "Is this a bug"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by paul88 on 2010-05-02
I am using 9.10.

Whenever I run the software update program, and then restart and load in to grub a new edition of linux is on the grub menu. I have looked into it and have found that i might be because of a new linux image may have been included in the update. If this is so should the other versions of the images from previous updates not be removed thus resulting in space not being used up, or do they need to be there.

I have found out that you can remove them manually but I am not very familiar with code being used (and feel that i would break grub). I think there should be an update included to remove the older versions from the menu.

Does anyone else think that this is a bug and should be reported, if so how is that done?

Or I am missing the point of the older versions of the same OS being in the menu?

---

### Post by WinterRain on 2010-05-02
It is not a bug, and they are intended to be there. I wouldn't worry about it, as they don't take up much room. They leave them there just in case the new kernel breaks something, and then it is easy to use a previous version. If it concerns you that much, you can remove them in synaptic. But I would leave them alone.

---

### Post by friv_livs on 2010-05-02
This is not a bug.

The reason ubu keeps it's old kernel versions is to provide a backup boot option in case the recent kernel version fails somehow.

It is generally advisable to keep two kernel versions, so you have a backup boot option.

As far as removal goes, Admin->Synaptic will let you remove old kernel versions. Just search in synaptic: "2.6.31-xx", where xx is the last two digits of the kernel version you want to remove.

For manual removal of remaining kernel versions, search "2.6.31-xx" in the file finder app, open a terminal, and run ```
sudo rm "filepath_in_finder"/"file_found"
```.

---

### Post by paul88 on 2010-05-02
OK just to be sure is the one on the top of the menu the newest version?

---

### Post by WinterRain on 2010-05-02
> **paul88 said:**
> OK just to be sure is the one on the top of the menu the newest version?

Yes.

---

### Post by lavinog on 2010-05-03
Computer janitor should offer to remove older kernels in 10.04.  This behaviour was removed in 9.10 due to a bug where packages were removed that shouldn't be.

---

