---
title: "sudoers error...."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-12-30
So i managed to mess up my sudoers file, on line 26 that read something like "%admin ALL = (ALL) ALL" or something like that, just writing that from memory. I kept a backup of the sudoers file before I edited it (and yes I was editing via visudo). So now I am a bit concerned because I no longer have the ability to gain root. Typing in sudo and then a command yields that there is an error in sudoers at line 26. I can't open the sudoers file to edit it, and I can't copy the backup over it either. I tried logging into the recovery console at the Grub boot menu and dropping to a root terminal, but even after a successful copy/edit of sudoers, I log back in without the ability to perform root actions....

---

### Post by Sarmacid on 2008-12-30
Maybe your user is no longer part of the admin group. What's the output of *groups*?

---

### Post by Jengajam2 on 2008-12-30
Try just using the "su" command to make your terminal root. Then replace 26 with the backup's line 26.

---

### Post by oldos2er on 2008-12-30
> **Jengajam2 said:**
> Try just using the "su" command to make your terminal root. Then replace 26 with the backup's line 26.

 Since there's no root account in Ubuntu, "su" alone won't work. "sudo su" will though.

 To the OP: boot from the LiveCD; you should be able to restore your backup copy of sudoers.

---

### Post by DoubleMcLovin on 2008-12-30
nvm.... the live cd worked out. took 2 reboots for some reason? that was weird. And also, very curious that line 26 was absolutely identical in the backup and the modified version, and the backup didn't give me an error. So odd. It was even identical down to the spacing O.o....

---

