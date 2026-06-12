---
title: "Messed up in Fstab...No options for Mounting drives"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by computerandu on 2011-08-15
Hi All,

Recently when i was trying to auto-mount my windows drive by editing fstab like this:  [COLOR=#ff0000][gksu]("http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features") gedit /etc/fstab[/COLOR]  

After editing when I saved and closed the fstab file it gave me following error in the terminal:

```

(gedit:1968): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BYMA0V': No such file or directory

(gedit:1968): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1968): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-u

```

**And my two NTFS partitions are not visible from then onwards. **

I tried solving it by manually making a directory: **/root/.local/share **but then this error is gone but the partitions are still not visible.

This is the content of my fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=b9a176e1-d122-4ea7-815b-555063d4e18f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=d7404e23-4d48-4bc1-ac9f-bbbc82806e02 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda8 during installation
UUID=8a3e328f-6394-4430-badb-5cd12a53731b none            swap    sw              0       0
#Auto-mounting of Windows drives: 01CB76F7F289ADE0
UUID=01CB76F7C2628FB0 /mount/WindowsDrive/105GB ntfs defaults,uid=1000 0 0
UUID=01CB76F7F289ADE0 /mount/WindowsDrive/45GB ntfs defaults,uid=1000 0 0

```

---

### Post by WyleECoyote on 2011-08-15
do the mount points exist? here is what I did for my spare drive:
```
UUID=f31270bf-efaa-49e2-a8dd-f0ac1802a4cb /home/myuser/Downloads ext3  auto,user,exec,rw  0	0
```

that gives all users access to it but I am the only user otherwise I would change the path and symlink my Downloads folder to it. instead of ext3 you just need to put in ntfs


btw, those Gtk-WARNINGS look unimportant just temp files not sure just treat them as they are 'warnings' if you don&#8217;t like to see them try gksudo instead of gksu

---

### Post by computerandu on 2011-08-15
Yeah...the mount points do exist...i can access them when i go from /root/mount/WindowsDrive/

but the problem is that these two partitions are not visible in the File Manager GUI...like when i open Home Folder there are various drives/partitions in the left pane...they are not there anymore...


any ideas?

---

### Post by Morbius1 on 2011-08-15
If you create a mount point in /home/user-name or /media they will show up all over the place - like the desktop. But if you mount them anywhere else like you have done then they won't.

Go to /mount/WindowsDrive/105GB and bookmark it in Nautilus - Bookmarks > Add bookmark.

---

