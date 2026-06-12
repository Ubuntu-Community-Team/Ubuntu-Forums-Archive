---
title: "Automounting question"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by donescamillo on 2009-10-01
Hi,

On my notebook I have one HDD split like this:

1. C:\-WinXP (NTFS)
2. D:\-my private data (NTFS)
3. linux-Ext3  

There is no swap partition, I will create a swap file later.
I wanted to have C and D  auto mounted at start up so I changed fstab as follows:

UUID=dc6e477a-ea4b-4bb9-a72d-fe48c7412150 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# mine additions
/dev/sda1     /media/C ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda5     /media/D ntfs-3g defaults,locale=en_AU.UTF-8 0 0

When I reboot they get automounted but when I open Nautilus all I see in the tree pane is:

Home Folder
File System
75 GB Media
31 GB media

Only when I run gksu Nautilus I see:

Home Folder
File System
C
D

How can I make Nautilus show them as C and D without gksu?

Thank you
donescamillo

---

### Post by nhasian on 2009-10-01
go to system->administration->partition editor
if you dont have it you can install it with:

```
sudo apt-get install gparted
```

right click on the partition and choose LABEL.  then set the label to whatever you like.

---

### Post by egalvan on 2009-10-01
You're better off doing the NTFS re-name under Windows, not Linux-GRUB.

it's a much simpler, safer matter.

And you can label them anything you want.
I would recommend not using spaces...

for instance...
use
data_drive


instead of 
data drive


Or call them C and D.


Me, I don't use capitals or spaces, it's the *nix way.

---

### Post by donescamillo on 2009-10-01
Hi,

The names C and D I gave to the partitions (by mounting them in folders called C and D). But the question is why when I run Nautilus with gksu it shows the partitions as C and D (or whatever names I give them) and when I run it as ordinary user it shows other names (like 75GB media)

regards,
donescamillo

---

### Post by theozzlives on 2009-10-01
> **donescamillo said:**
> Hi,

The names C and D I gave to the partitions (by mounting them in folders called C and D). But the question is why when I run Nautilus with gksu it shows the partitions as C and D (or whatever names I give them) and when I run it as ordinary user it shows other names (like 75GB media)

regards,
donescamillo

Try labeling them as mentioned, I have a SD card labeled NO_LABEL and it shows as such.

---

### Post by donescamillo on 2009-10-01
I can rename them easily. But why in one case (no superuser) they are shown with one name and  in another case shown with another name?

regards,
donescamillo

---

### Post by donescamillo on 2009-10-01
What I found is this:
Nautilus shows in the tree panel the volume names.
When I run Nautilus as a normal user the volume names are "75GB Media" and "31 GB Media". 
When I run Nautilus with gksu, the volume names are the names of the folders where I mounted these two partitions, namely C and D.
This is not a problem, I guess this is how Linux works, but why the volume names are different depending on which user reads them I dont know. Apparently I have to read some on the topic.

regards,
donescamillo

---

