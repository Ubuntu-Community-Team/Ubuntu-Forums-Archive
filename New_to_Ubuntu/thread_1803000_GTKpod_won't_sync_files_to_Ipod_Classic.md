---
title: "GTKpod won't sync files to Ipod Classic"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by Kalish on 2011-07-12
I recently made the switch from Windows to Ubuntu 10.4 and have been trying to use GTKpod to manage my 160 gb Ipod Classic. I've gotten some files set up in the GTKpod library to sync over to the empty Ipod and pressed the &quot;Save Changes&quot; button, ejected and unmounted, but none of what was in my library actually moved over to the Ipod, it is still entirely empty. I looked up what might be causing this specific problem and the only explanation I could find was that the computer could not find the Ipod's Firewire, so I followed the second set of instructions at http://gtkpod.wikispaces.com/Sysinfo+File#ClassicNano3g. At this point, I know the Ipod has been mounted and I know that it has found the Firewire, but it still will not actually move any files over to the Ipod. I'm sure there's probably some very easy solution to this, but I cannot find it. Any help is much appreciated!

---

### Post by jtarin on 2011-07-12
In your /etc/fstab check the filesystem for your ipod see that is is mounting as vfat.

---

### Post by LowSky on 2011-07-12
I find Banshee to work great with my 80Gb model.

---

### Post by Kalish on 2011-07-13
> **jtarin said:**
> In your /etc/fstab check the filesystem for your ipod see that is is mounting as vfat.

Ok, here's what it says in my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8069cd22-224f-4412-b489-0dfc22efe5d7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Not sure how to tell whether or not it is mounted as vfat, but the Ipod was previously synced with Itunes in Windows XP, so it should automatically be vfat, right?

---

### Post by Kalish on 2011-07-13
SOLVED - Everything was OK with the system, just a misunderstanding on my part. I thought that pressing the Save Changes button was like the Sync button in Itunes, that it would automatically move over all the files to the Ipod. Now I know you have to highlight the files you want and then move them to the Ipod and THEN press Save Changes. It's working fine now, thanks for your help, guys!

---

