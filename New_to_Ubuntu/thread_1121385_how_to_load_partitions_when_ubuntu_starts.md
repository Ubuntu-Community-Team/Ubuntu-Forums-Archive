---
title: "how to load partitions when ubuntu starts"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by chethankrish on 2009-04-10
i have 3 partitions in my system. C: , D: , E: .. whenever i start ubuntu D: and E: partitions does not get loaded. i have to manually load them every time i restart my computer. could you please help me by letting me know if i have any way to ask ubuntu automatically load these partitions when it starts.. thank you.

---

### Post by fabricator4 on 2009-04-10
You could write a script that mounts the volumes, then put that script in your startup.  I haven't got this far myself yet.  The startup is in System->Preferences->Session 

There's probably a better way to do it, which I hope someone will point out, such as a place to put scripts so they run at startup.

Chris

---

### Post by tjwoosta on 2009-04-10
edit your /etc/fstab 

this file is what controls which partitions are automounted, what permissions they have, and what mountpoints they use, etc


this should help
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")


also to find the UUID of partitions you can use the blkid command

```
blkid
```

---

### Post by zeex on 2009-04-26
> **chethankrish said:**
> i have 3 partitions in my system. C: , D: , E: .. whenever i start ubuntu D: and E: partitions does not get loaded. i have to manually load them every time i restart my computer. could you please help me by letting me know if i have any way to ask ubuntu automatically load these partitions when it starts.. thank you.

Take a look at [**_this_**]("http://stringofthoughts.wordpress.com/2009/04/16/auto-mount-window-drives-at-startup-ubuntu-810/"). I have this script works fine for me. It doesn't mount NTFS drives if windows hasn't been closed properly. You need to shutdown windows properly. do that and this script works flawlessly.

---

### Post by 4Orbs on 2009-04-26
You might give Storage Device Manager a try. It is just a nice gui for fstab that makes mounting, unmounting and permissions one click and apple pie. It's listed in Synaptic Package Manager as pysdm.

---

### Post by powel212 on 2009-04-26
This is the easiest and best way I know of. Easy GUI method. No scripts or messing around with text files.

Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications"

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to; enable read and write to internal and external drives.

the next time you boot all your drives will appear on the desktop.

I hope that helps.

Powel

---

### Post by presence1960 on 2009-04-26
> **chethankrish said:**
> i have 3 partitions in my system. C: , D: , E: .. whenever i start ubuntu D: and E: partitions does not get loaded. i have to manually load them every time i restart my computer. could you please help me by letting me know if i have any way to ask ubuntu automatically load these partitions when it starts.. thank you.

we all know what you mean but Linux does not label partitions as C:, D:, etc. The first drive is sda with numbering for partitions following sda. Here is an example:

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        4569    15727635   83  Linux
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18389   147709611   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
raz@raz-desktop:~$ 

Note I have two HDD with various partitions. This is how we do it in Linux. C:, D:, etc is a Windows thing. If you run > sudo fdisk -l from terminal you will see the designations in Linux of the drives you are referring to as C:, D;, E:. Note that is a lower case L in that command for terminal.

---

