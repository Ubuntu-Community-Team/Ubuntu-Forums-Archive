---
title: "[SOLVED] mounting/wiping"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-13
Using 8.10 server. After mounting drives, how do you wipe them? They currently have ntfs partitions. Thanks

---

### Post by Rolcol on 2008-12-13
> **pshootr said:**
> Using 8.10 server. After mounting drives, how do you wipe them? They currently have ntfs partitions. Thanks

How exactly do you want to wipe it?  Do you want to permanently remove everything while keeping the partition information or do you want to shred the partition info as well?

Try looking up the shred command.```
man shred
```

---

### Post by mkvnmtr on 2008-12-13
You can use Gparted. If you have it on your system you can use it on the drive when it is not mounted. If you dont't have it on your system you can use it off of a live disk. The Ubuntu desktop live disk has it or you can download a gparted live disk. This will reformat. If you need to wipe it as in remove everything there is a program to write 0 and 1 about thirty times and this will wipe it. Then you will need to reformat it with gparted. The wiping program is in the package manager but I forget the name. I am sure you can do a search in the package manager for"wiping drive" and find it if someone dosn't post before you can do a search.

---

### Post by Rolcol on 2008-12-13
> **mkvnmtr said:**
> You can use Gparted. If you have it on your system you can use it on the drive when it is not mounted. If you dont't have it on your system you can use it off of a live disk. The Ubuntu desktop live disk has it or you can download a gparted live disk. This will reformat. If you need to wipe it as in remove everything there is a program to write 0 and 1 about thirty times and this will wipe it. Then you will need to reformat it with gparted. The wiping program is in the package manager but I forget the name. I am sure you can do a search in the package manager for"wiping drive" and find it if someone dosn't post before you can do a search.

You're probably thinking of secure-delete.  secure-delete has more features than just "shred".  Secure-delete can recursively delete folders unlike just plain "shred".  ```
sudo apt-get install secure-delete
man srm
```

Secure-delete just shreds the files.  You can shred the whole partition (it will need formatting) with shred.

**Edit:** You can try this command after it's mounted to permanently remove these files```
srm -rvz /path/to/ntfs/drive

```

Replace '/path/to/ntfs/drive' with the location of the mounted drive.

---

### Post by The Cog on 2008-12-13
You must unmount them before reformatting or deleting the partitions. gparted is probably the easiest program to use. it can also create new partitions or reformat existing ones with different filesystems.

---

### Post by jimmy the saint on 2008-12-13
If you want to wipe the disk, look into Dban (Derick's boot n nuke).  Just google it.  Essentilly, you will create a bootable floppy or cd, make sure that the disk you want wiped is the ONLY drive attached to the system (just unhook the others) and run the program.  Your drive will be so clean only super men-in-black types can even theoretically recover anything.

---

### Post by pshootr on 2008-12-13
Thanks alot guys for your help.):P

---

