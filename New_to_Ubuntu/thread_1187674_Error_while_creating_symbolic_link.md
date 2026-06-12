---
title: "Error while creating symbolic link"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by wolfv6 on 2009-06-14
[FONT=Arial][SIZE=2]I tried to create a symbolic link to my “Profiles” folder.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]The folder's permissions are displayed in the attached screen shoot.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Is there a permissions problem or is it something else?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]I could not change the Folder accesses.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Ubuntu is on an ext3 partition while the “Profiles” folder is on a FAT32 partition.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]I am using Nautilus 2.26.2 on Ubuntu 9.04[/SIZE][/FONT]
[SIZE=2]
[/SIZE]
[FONT=Arial][SIZE=3][SIZE=2]Thank you.[/SIZE][/SIZE][/FONT]
[FONT=Arial][SIZE=3]
[/SIZE][/FONT]

---

### Post by mprince on 2009-06-15
FAT32 doesn't support symbolic links.

---

### Post by SoftwareExplorer on 2009-06-15
> **mprince said:**
> FAT32 doesn't support symbolic links.

On a side note, I think that NTFS does. MS Windows calls them 'junctions'. So if you are trying to have a partition to get files between Ubuntu and windows, NTFS could be the way to go.

---

### Post by wolfv6 on 2009-06-17
Thanks for the help.  I  got Firefox's on Windows and Firefox on Ubuntu to share the same profile folder.  Here is how I did it:

I converted Windows FAT32 partition to NTSF.  Then I found Ubuntu Firefox's profiles.ini file and edited it's IsRelative and path values as described in [http://support.mozilla.com/en-US/kb/Backing+up+your+information#Restoring_to_a_different_location](http://support.mozilla.com/en-US/kb/Backing+up+your+information#Restoring_to_a_different_location)
 
The new path points to the Widows Firefox's Profile file.  I tested read & write of book marks and it worked!

---

