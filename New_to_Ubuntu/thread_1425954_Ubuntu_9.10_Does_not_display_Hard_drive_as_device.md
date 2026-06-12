---
title: "Ubuntu 9.10 Does not display Hard drive as device"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Aster-Phoenix on 2010-03-09
Hello i recently got Ubuntu on my machine, since I got it it has not displayed my hard drive in computer. I thought it fix itself sooner or later but it hasn't. The hard drive is connected because I can see my files in file-system but i cannot access my hard drive. I believe its not mounted correctly. Could anybody help?

---

### Post by gmjs on 2010-03-09
Just to confirm, when you open **Places > Computer** from the GNOME menu, there is no **'Filesystem'** option (along with perhaps a CDROM Drive and/or Floppy Drive icon)?

---

### Post by Aster-Phoenix on 2010-03-09
> **gmjs said:**
> Just to confirm, when you open **Places > Computer** from the GNOME menu, there is no **'Filesystem'** option (along with perhaps a CDROM Drive and/or Floppy Drive icon)?
No i see filesystem but i do not see my 40gb hard drive.

---

### Post by gmjs on 2010-03-09
The **Filesystem** icon **is** the hard drive.  It's mounted to the path '**/**'

For reassurance of this, you can view the disk partition information with the following command at the terminal (**Applications > Accessories > Terminal**):

```
**sudo fdisk -l**
```

(password at the prompt)

It'll tell you a bit about the drive, along with it's device file name and size.
[COLOR="DarkRed"]
(Also: Please be careful with the 'fdisk' command!)[/COLOR]

---

### Post by Aster-Phoenix on 2010-03-09
> **gmjs said:**
> The **Filesystem** icon **is** the hard drive.  It's mounted to the path '**/**'

For reassurance of this, you can view the disk partition information with the following command at the terminal (**Applications > Accessories > Terminal**):

```
**sudo fdisk -l**
```(password at the prompt)

It'll tell you a bit about the drive, along with it's device file name and size.
[COLOR=DarkRed]
(Also: Please be careful with the 'fdisk' command!)[/COLOR]
Oh lol I'm an ignit xD
Thanks.

---

### Post by gmjs on 2010-03-09
No ;) just new to the GNOME desktop!  Other hard disk drives would appear in there if there were more drives, or if it were partitioned.

Unlike with Windows, external drives (USB drives etc.) don't show up in 'Computer' though.  These fit into the filesystem in the **/media** folder (and of course a launcher is placed on the Desktop).

Hope you're enjoying Ubuntu!

---

