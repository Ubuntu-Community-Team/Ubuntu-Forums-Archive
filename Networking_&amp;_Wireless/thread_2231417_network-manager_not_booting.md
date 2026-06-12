---
title: "network-manager not booting"
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by tendouser on 2014-06-25
I can't boot from my usb stick lubuntu 14.04 persistant   
[53.184999] ext4-fs error (device loop1): ext4_lookup: 1437: inode#654797: comm NetworkManager: deleted inode referenced 655387
[53.185254] same
[53.185343] same

any help with this?

:(:confused:

---

### Post by varunendra on 2014-06-26
> **tendouser said:**
> [53.184999] **ext4-fs error** (device loop1):

I don't think the rest of the error message matters, an 'fs error' most probably means a corrupt filesystem, resulting in corrupt component(s), whichever falls in that area.

The mounted loop device that has this error should be the 'casper-rw' file created for persistence. The solution in short is to simply re-create the Live USB.

A bit trickier solution is to boot without 'persistent' flag. I can explain how to do that, but recreating the live usb is simply the easiest solution.

---

### Post by tendouser on 2014-06-26
is there a way to fix this corrupted casper-rw?

thanks!

---

### Post by varunendra on 2014-06-26
It is just my guess, and I could be wrong. Is there something important in the 'persistent' area that you want to save? If yes, I think it is easy to mount it (not sure, may have to experiment).

If not, and you just want the persistence, recreation process will automatically create a fresh one. You can also copy an already created one from another live USB (may cause problems if copied from a different version of Ubuntu).

If you just want to avoid the hassle of recreating the live USB (shouldn't take more than 10 minutes though), you can - 1) either create a 'casper-rw' partition, keeping the filesystem 'ext3/4', or 2) just copy a fresh 'casper-rw' file from somewhere (from the same version of Ubuntu live).

Let me know your reason and preference, and I'll try to help as much as I can.

By the way, to confirm **whether it is indeed the persistent file or not**, you just need to boot without the 'persistent' flag. You can remove it temporarily for just one session for a test (easy, automatically back on next boot), or permanently (easier, can be reverted).

To remove it temporarily, press any key as soon as you see the purple blank screen with only a tiny icon at the bottom during boot. This will get you to advanced boot menu. After selecting the language, press 'F6' followed by 'Esc'. This will cause the kernel boot line to appear on the screen (above the "F1, F2.." etc. menus at the bottom) which you can edit using arrow keys (to move the cursor) and 'Del', 'backspace' etc keys. Look for the term 'persistent' and delete it, then press 'Enter' to boot.

To remove it permanently, you must edit the file that provides the kernel boot line. Action is same - just remove the word "persistent" from the boot line, but the location of the correct file depends on the method used to create the live USB.

---

### Post by tendouser on 2014-06-26
yes it is the persistent file ...I did try and did boot succesfuly without it!

man is there no way to fix that casper-rw file?

I did some package installations to have some additional software like LAMP server phpmyadmin etc.

If there is not ...that's sad

---

### Post by varunendra on 2014-06-26
Problem is, filesystem repair utilities like 'fsck' work on block devices, like raw partitions, not on files containing virtual filesystems. I may be wrong due to limited knowledge here, so you may search yourself to see if a loopmounted filesystem, or the file containing the virtual filesystem can be repaired.

If not, we can still try loopmounting the casper-rw file, and copy the packages you downloaded so that you don't have to download them again. The installed packages (if installed from .deb packages) are cached in /var/apt/archives directory. We can also try copying entire contents of the mounted filesystem (some contents may not be copied due to being in corrupt areas) and restoring them into a fresh casper-rw file when it is mounted. Although both these approaches may be more cumbersome than creating a fresh Live USB and re-installing the packages normally.

Not useful in this case, but in future, you can keep your persistent area safe by simply backing up a copy of this casper-rw file while it is working.

---

