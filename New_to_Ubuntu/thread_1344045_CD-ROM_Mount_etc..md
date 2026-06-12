---
title: "CD-ROM Mount etc."
date: 2009-12-02
forum: New to Ubuntu
---

### Post by hoopsterj2 on 2009-12-02
I've been reading about this, and I'm still not sure how to get cd-rom to autorun, xubuntu 9.10. I have the following info, but not sure how to proceed. Any help much appreciated:

                                  0  dev='/dev/scd0'    rwrw-- : 'TOSHIBA' 'DVD-ROM SD-C2302'
 

 ~$ cat /etc/fstab /etc/mtab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda1 during installation 
 UUID=5943ff00-a242-41ab-8a29-478cb7147225 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=f0c47240-85b7-40a6-9349-f358cf7f343a none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 /dev/sda1 / ext4 rw,errors=remount-ro 0 0 
 proc /proc proc rw 0 0 
 none /sys sysfs rw,noexec,nosuid,nodev 0 0 
 none /sys/fs/fuse/connections fusectl rw 0 0 
 none /sys/kernel/debug debugfs rw 0 0 
 none /sys/kernel/security securityfs rw 0 0 
 udev /dev tmpfs rw,mode=0755 0 0 
 none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 
 none /dev/shm tmpfs rw,nosuid,nodev 0 0 
 none /var/run tmpfs rw,nosuid,mode=0755 0 0 
 none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0 
 none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0

---

### Post by llamabr on 2009-12-02
automount, or autorun?  If the former, it should, according to your fstab.  What does it not do?

if the latter, what do you mean, autorun?

---

### Post by hoopsterj2 on 2009-12-02
thanks for the quick reply. i may have botched things up, b/c i got info, and changed things for sound and wifi ... and then did not take a real direct / proven route to playing media.

so at this point i'm not sure what i've done. one thing that may be wrecking things is that I've made 2 attempts, through synaptic to, uninstall totem, in favor of vlc (not sure why totem reappeared and tried to play the 1 dvd put in, after synaptic uninstalled. I've also copy and pasted code from experts that worked in my install of ubuntu 9.10 on another machine. I have insterted commercial cd and dvd to see howthose 2 would do. it could be that i've not followed the instructions correctly.

at the moment, vlc sees a music cd and does nothing, and the dvd is seen, media/cdrom0 (icon on desktop has movie title), but i double click on it and i only see 2 files on desktop audio ts and video ts.

clearly i did a better job with wifi, sound, and media playing with ubuntu than with xubuntu!

---

