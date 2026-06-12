---
title: "Sharing folder &quot;/share&quot; how to?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-04
Hi, I recently installed 9.0.4 on my laptop it works great.
While partitioning I made a 16GB logical partition and mounted it to /share. (as FAT32, but shows as vfat in gnome system manager)

Then when install was complete I logged on right-clicked the /share folder and tried to use the share-options.
At first it needed to install so it did that. I then restarted the computer and went back to apply the share options.

But this is what comes up.
> Nautilus needs to add some permissions to your folder "share" in order to share it
The folder "share" needs the following extra permissions for sharing to work:
  - read permission by others
  - write permission by others
  - execute permission by others
Do you want Nautilus to add these permissions to the folder automatically?I click add automatically.

And then this happens...
> Could not change the permissions of folder "share"How can I overcome this problem?
Can I go into terminal and execute the same sharing options w/ root permissions?

The options are to let guest view and allow read/write.

Thanks in advance.

[EDIT] Is it some type of vuln if I allow sharing to that folder?
/share ..

---

### Post by zerhacke on 2009-09-04
You probably don't have ownership of the folder in order to share it.

man chown in a terminal will teach you how.

---

### Post by JillSwift on 2009-09-04
You probably don't have samba server installed.

```
sudo apt-get install samba
```should install what you need :)

---

### Post by achase79 on 2009-09-04
Fat32 is only nessicary for sharing a partition in a dual boot setup.  If you are just sharing a folder on your network you will need samba and should have the folder on a linux partition (fat filesystems don't let you set permissions like linux and NTFS does)

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-04
> **achase79 said:**
> Fat32 is only nessicary for sharing a partition in a dual boot setup.  If you are just sharing a folder on your network you will need samba and should have the folder on a linux partition (fat filesystems don't let you set permissions like linux and NTFS does)
How would I go about re-partitioning the /share partition? Would it affect the system at all or just that partition?

Thanks. Also, if I have windows desktop and linux laptop, would they both be able to interact on a ext3 partition? (read/write files)

> You probably don't have samba server installed.
It is installed.

------------------------------------
EDIT
------------------------------------
Okay I found the program to partition, i used gpart.
Then i re-mounted the partition to /share.

Now I need to get ownership permissions to change share settings.

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-04
> **zerhacke said:**
> You probably don't have ownership of the folder in order to share it.

man chown in a terminal will teach you how.
Didn't know what you meant, thanks.
sudo chown -R yourusername /path/to/directory

---

