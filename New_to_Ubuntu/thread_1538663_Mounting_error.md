---
title: "Mounting error"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Souptik on 2010-07-25
I have installed Lucid for a few months on my laptop. Just now after updating Ubuntu using the update manager, the start-up screen comes up with a message- "failed to mount /home. Press skip to skip mounting or M for manual recovery." Any help on this regard will be appreciated.

---

### Post by cariboo on 2010-07-25
What does the /home entry in /etc/fstab look like? Are you mounting by device label or UUID?

---

### Post by Souptik on 2010-07-27
> **cariboo907 said:**
> What does the /home entry in /etc/fstab look like? Are you mounting by device label or UUID?
Here is the configuration of etc/fstab. Personally i can't make neither head nor tail of it.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=49709c62-d6e0-472d-93f4-4a193d83871a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=341e657a-1ea6-4eb6-9285-80c1b4b01b85 none            swap    sw              0       0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/home    /home    dazukofs
# ... DazukoFS

---

### Post by Souptik on 2010-08-02
my first message was wrong... sorry abt that. it's press S to skip mounting not skip to skip mounting sorry... that's probably why i did not get a reply...:(

---

