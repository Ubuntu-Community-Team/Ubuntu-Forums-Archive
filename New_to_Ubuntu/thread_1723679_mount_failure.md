---
title: "mount failure ?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by nnjond on 2011-04-07
Hi,

I can select Ubuntu 10.10 OS from the grub menu, but it no longer loads? It scrolls through some lines, including mount failure and "No such file or directory." before halting below :

(initramfs)


The same happens when recovery is selected.

Any advice please?

---

### Post by 1991sudarshan on 2011-04-07
Did you happen to do any change to the hard disk?

---

### Post by nnjond on 2011-04-07
Thanks for your interest. I'm trying to repair the grub from a live cd, but I can't out the passwd

---

### Post by Rubi1200 on 2011-04-07
Posting the results of the boot script would help us to help you:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

