---
title: "How To Share Swap File Between Two Distros"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-30
I have a triple boot going on, have OSX, XP, and Ubuntu 8.10 installed. Well I'm thinking about adding EasyPeasy distro. Anyway for this new distro I created a new partition (ext3 \ mount point). Now I read that I don't need to create a new swap partition. But when I go through the install procedure it says its gonna format my current swap partition (for Ubuntu 8.10), is this okay? Or is there another method to allow them to share swap files?

---

### Post by cdtech on 2009-01-30
It's Ok. Swap is a Swap. Same as using a file for Swap, it's just an empty file.

---

### Post by taurus on 2009-01-30
You could allow that installer to reformat the swap partition but then you need to change the UUID entry in /etc/fstab (from Ubuntu) to reflect the new one since the UUID would change.  However, you have an option not to allow it to format the swap partition and you can add an entry for it in /etc/fstab once you have installed EasyPeasy!

---

### Post by RookieUbuntuUser58 on 2009-01-30
> **taurus said:**
> You could allow that installer to reformat the swap partition but then you need to change the UUID entry in /etc/fstab (from Ubuntu) to reflect the new one since the UUID would change.  However, you have an option not to allow it to format the swap partition and you can add an entry for it in /etc/fstab once you have installed EasyPeasy!

Where's the option to not allow it to format the swap file? I'm at the last step in the install process. I click advanced and it has nothing about stopping the formatting, only about installing the boot loader (which I unselected since I don't want to overwrite the current Grub bootloader).

---

### Post by taurus on 2009-01-30
If there is no option to skip it, then format it.  Then, get into Ubuntu and look for the new UUID so you can modify it in /etc/fstab.

```
sudo blkid
```

---

