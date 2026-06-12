---
title: "Mount NTFS on boot?"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Slow Motion on 2010-07-25
Hello,

Ubuntu does a great job at mounting my NTFS volume when I open it, but I have shortcut folders to my documents on the NTFS volume that won't display under my "places" menu unless I open the NTFS volume first. How can I get my NTFS volume to mount on boot, so my shortcuts are displayed in the "Places" menu?

---

### Post by nerdtron on 2010-07-25
Open Synaptic Package Manger and then search for the ntfs-config tool. Install it and unmount the NTFS partitions first. Run the tool and enable read/write of NTFS partitions and there should be an option to mount volumes upon reboot. Restart ubuntu, if all goes well the partitions are mounted by default.

---

### Post by Locke_99GS on 2010-07-25
NTFS has had full read/write support in Ubuntu by default for the last couple of years.

Simply add the mount to your /etc/fstab, and reboot. No need to add extra cruft.

---

### Post by oldfred on 2010-07-26
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

After you understand a little about the settings to use which are options here then this is the easy way:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

