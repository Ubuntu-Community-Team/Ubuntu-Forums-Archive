---
title: "Live CD isn't working, recieving BusyBox?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-31
I'm trying to boot into the Live CD version of 8.10 so I can repartition my main HDD so I can dual-boot windows XP.

Now, I had this error when first trying to run the Live CD a month ago and afteer three tries it just "worked". However, this time, I continually receive the following:

1) BIOS boots up fine.
2) The Ubuntu screen comes up great with "Try Ubuntu without affecting this computer" and other options.
3) I select The first option (aka Live CD) and it shows me the orange rectangle bouncing back and forth in the loading bar with "ubuntu" at the top.
4) The screen goes black for a second and shows me: 
"Loading, please wait...

BusyBox 1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)"

Now, I had this once before, but I just retried the entire process three times and it just worked. I cannot make this work! What exactly am I doing wrong? I've done a lot of research and cannot find a single answer that works.

---

### Post by mattbutsko on 2009-01-31
Fixed it. Nevermind.

Pressed F6 twice at the boot screen for trouble shooting and selected no acpi.

---

