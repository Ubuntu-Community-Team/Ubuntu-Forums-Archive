---
title: "how to play a UDF dvd?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by rocker-billy on 2011-04-07
Was hoping to watch a film on a dvd but Movie Player or Parole Movie Player will not play it? I did check and saw it had a UDF file extension. Could anyone tell me how i might get to play the dvd please.

---

### Post by Wobblybob on 2011-04-07
The last time I saw one of hese DVD's was from a VISTA backup, try this thread [[COLOR="Navy"]http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/[/COLOR]]("http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/")

---

### Post by rocker-billy on 2011-04-07
Hello Wobblybob, found my way to the fstab file but can't make head nor tail of its contents.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6f7490a-986d-4c05-916c-02d7898c5cc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e4f1a14a-6eb8-4acd-937e-b3572e269cd2 none            swap    sw              0       0

---

### Post by Bölvaður on 2011-04-07
Is the problem that you cannot mount it or you cannot play it?

If the problem is that you cannot play it:

[http://ubuntuforums.org/showthread.php?p=10645388](http://ubuntuforums.org/showthread.php?p=10645388)


If the problem is that you cannot mount it:

> **rocker-billy said:**
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6f7490a-986d-4c05-916c-02d7898c5cc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e4f1a14a-6eb8-4acd-937e-b3572e269cd2 none            swap    sw              0       0
**/dev/scd1          /media/cdrom0    [B]auto    **user,noauto        0          0[/B]



add the bottom line like the website says. But Im not sure this will work as your fstab does not list cd drive, so it might  be correct way to mount the cd with certain tags like ware writing here in fstab.
But try adding this one line and restarting your computer (probably possible to avoid it by just logging off and on, but I guess you want to be 100% sure right now).

you can edit fstab many ways. my favorite way is just to
alt + F2 and write ```
gksu nautilus /
``` so I can just browse to any file and edit them as root


or alt + F2 and write ```
gksu gedit /etc/fstab
``` which gives you root access (graphical sudo = gksu) with the gedit text editor to the file you open which is /etc/fstab


do this and report back.

---

### Post by rocker-billy on 2011-04-07
Hi Bolvadur, did exactly as you suggested except i substituded scd1 for sda1. I saved the file and then restarted my computer but it still wouldn't play the dvd?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6f7490a-986d-4c05-916c-02d7898c5cc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e4f1a14a-6eb8-4acd-937e-b3572e269cd2 none            swap    sw              0       0
/dev/sda1 /media/cdrom0 auto user,noauto 0 0

---

### Post by Bölvaður on 2011-04-08
> **rocker-billy said:**
> Hi Bolvadur, did exactly as you suggested except i substituded scd1 for sda1. I saved the file and then restarted my computer but it still wouldn't play the dvd?

Then you arent mounting your dvd player, you must change it like already stated.
Is this an image of a dvd you got on your computer that you want to mount, or is this a physical dvd?

---

