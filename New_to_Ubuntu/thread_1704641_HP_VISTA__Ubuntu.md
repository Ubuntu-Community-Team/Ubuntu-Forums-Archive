---
title: "HP VISTA / Ubuntu"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by adduds on 2011-03-10
This is the story my gf liked ubuntu so i installed it on her computer a HP DV7 deleted all partitions and formated 360GB to ext4

she's used it for a bit but figured just incase she runs into troubles she'd like vista (what her computer came with) 

so used gparted created a 90gig partition formated to NTFS

when i'm in the vista installer disk selecting what partition to install vista on it says

"windows cannot find a system volume that meets requirements for installation"

using the installer i've deleted it, created a partition, formatted it, made sure usb was not bootable before the hard disk in bios (as this can be an issue)

is it a primary partition problem with ubuntu?

---

### Post by owiknowi on 2011-03-10
you'll need to set the ntfs partition flag to 'boot'.
boot gparted, select the ntfs partition, right click on it and select flags and mark 'boot' option.

hope this solves the problem.

regards from holland

---

### Post by adduds on 2011-03-11
Thanks very much that worked lol I figured it was something silly like that!

thanks from canada:KS

---

