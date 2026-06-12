---
title: "Boot problems"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by POWMS on 2008-12-21
My notebook with dual boot XP and Xubuntu is not booting up each time I start up. I get a boot screen, 'Boot from harddrive, CD or floppy'. The harddrive is not booting when I choose it.
This coincidentally started happening after the major Xubuntu update 2 weeks ago.
If I turn the comp off and back on again it will boot up as usual.
Is my hardrive about to fail completely or is Xubuntu to blame?
Thanks

---

### Post by IamReck on 2008-12-21
Do you see anything when you choose to install from Hard drive?  Not even GRUB?

---

### Post by POWMS on 2008-12-21
If memory serves me correct, I get the makers logo then a dos screen with checking drives, no bootable CD present, then I usually get a boot screen showing XP and Xubuntu. I pick either and it continues on.
I am only getting to 'no bootable CD present' then a grey boot screen asking for a choice of bootable options. When I highlight boot from harddrive I get back to the grey screen again...........
Turning the copm off with the power switch will usually be successful.
But I feel this maybe the begining of the end......

---

### Post by caljohnsmith on 2008-12-22
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

