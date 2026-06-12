---
title: "So I screwed up. (grub error 17)"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by grungebunny on 2009-03-30
Hello and thanks in advance for the help!

I got myself a new laptop Vista preinstalled. First thing I do is whip out my cd of 8.10 and partition the HD and install Ubuntu.

A few reboots later and things are still fine.. Till I try to boot back into Vista. I get an error.. Reboot.. I have Grub error 17.
Long story short I ended up formatting the HD and reinstalled it back to its factory state with the CD.

I'm about to reinstall Ubuntu so i'm asking what can I do now to avoid this grub error 17? Also its a 64 bit laptop, should I use 64 bit Ubuntu?

Thanks!

---

### Post by grogo on 2009-03-30
Step 1: Use Vista's partitioner to shrink the partition as much as possible (may need to use PerfectDisk or another 3rd party defrag utility to move the MFT).  You want to use the partition resize within vista to ensure that it's a non-destructive resize as the linux utilities may FUBAR your NTFS partition as you've seen.

Step 2: Decide on 32 / 64 bit.  If you've got more than 3 GB of RAM you'll probably want to go with a 64 bit install, otherwise, it's a matter of what you're using the computer for... 

Step 3: Install

Step 4: Enjoy :)

PS.  Ensure to check for BIOS updates if it's an HP

---

### Post by presence1960 on 2009-03-30
> **grungebunny said:**
> Hello and thanks in advance for the help!

I got myself a new laptop Vista preinstalled. First thing I do is whip out my cd of 8.10 and partition the HD and install Ubuntu.

A few reboots later and things are still fine.. Till I try to boot back into Vista. I get an error.. Reboot.. I have Grub error 17.
Long story short I ended up formatting the HD and reinstalled it back to its factory state with the CD.

I'm about to reinstall Ubuntu so i'm asking what can I do now to avoid this grub error 17? Also its a 64 bit laptop, should I use 64 bit Ubuntu?

Thanks!

After the install boot into Ubuntu and check your menu.lst file: open a terminal and run this ```
gksu gedit /boot/grub/menu.lst
```

Make sure your windows entry has the correct entry:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows Vista
root		(hdx,y)
savedefault
chainloader	+1


edit line 2 to your windows partition

line 4 : where x is the number of your hard disk and y is the number of the partition of that HDD. The numbering starts with 0. Thus the first partition on the first HDD would be hd(0,0).

I have found on quite a few dual boot installs that the windows entry needs to be edited in menu.lst

---

