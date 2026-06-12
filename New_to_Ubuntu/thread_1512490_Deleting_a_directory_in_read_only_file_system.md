---
title: "Deleting a directory in read only file system"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by guru boy on 2010-06-18
Hi all
I have a 4 GB moserbear flash drive
I want to delete a directory from the drive 

so i used the command
[SIZE="3"][/SIZE]***_sudo rm -r DIR_NAME* _***

i used * as the dir. name contained spaces and command recognized it as multiple name;

**[SIZE="5"]but it prompts me a message[/SIZE]** 

*rm: cannot remove directory `GetDataBack for FAT and NTFS v4.0.0.1 Portable': Read-only file system*

please tell me how to remove it, and what is the reason behind the message

Regards
Guru

---

### Post by warfacegod on 2010-06-18
Use Synaptic and get ntfs-progs.

---

### Post by Flimm on 2010-06-18
There might be a physical lock button on the flash drive. SD cards and floppy disks have them. Try changing the button to "unlocked".

---

### Post by warfacegod on 2010-06-18
> **Flimm said:**
> There might be a physical lock button on the flash drive. SD cards and floppy disks have them. Try changing the button to "unlocked".

I've never heard of a USB jump drive having a lock button. Worth a look though.

---

