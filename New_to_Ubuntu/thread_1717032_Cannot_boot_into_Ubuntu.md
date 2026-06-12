---
title: "Cannot boot into Ubuntu"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Miter_J on 2011-03-29
Right after my choice of entering Ubuntu in lilo, the screen stuck there showing info like:
>  RAMDISK:Couldn't find valid RAM disk image starting at 0.
VFS: Cannot open root device "805" or unknown-block(8,5)
Please append a correct "root=" boot option. Here are the available partitions: (In fact, nothing was listed here)
Kernel panic- not syncing:VFS: Unable to mount root fs on unknown-block(8,5)
Pid:1,comm: swapper not tainted 2-6.35-22-generic #33-Ubuntu
Call Trace:
......


Anyone knows what happened here? This is the first time I meet such a situation... :confused:

---

### Post by Miter_J on 2011-03-29
I just used it and rebooted into Windows and then these errors took place...
I didn't do anything that might harm this machine
So really confused about this :(

---

### Post by Miter_J on 2011-03-30
AhAhAh!!!
Please help me out!!!

Plz plz plz!!!!!!!!!!!!!!!!
Somebody plz help me!!!

Don't ignore me:cry::cry:

---

### Post by Rubi1200 on 2011-03-30
Hi,
2 things we need please:

1. the specifications for the computer

2. the boot script results:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Miter_J on 2011-03-30
Oh, I've no live CD right now.

I would burn a live USB, maybe tomorrow(Sorry, I'm in China), and I'll come back to u.
Thanks in advance :)

---

### Post by Rubi1200 on 2011-03-30
Okay, no problem. I will look back in on the thread tomorrow.

---

