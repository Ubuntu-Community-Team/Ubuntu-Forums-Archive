---
title: "problem with swap partition"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-02-08
Last night I had a swap partition that was 5 gigabytes. Botted from the Live CD and resized it to 2gig. now the system doesn't seem to even be using it (on my conky it says no swap) how do I enable the swap file again?

---

### Post by taurus on 2009-02-08
When you resize or reformat the swap partition, the UUID would change to you need to get the new UUID and replace the old one in /etc/fstab with the new one.

Look for UUID:
```
sudo blkid
```

Edit /etc/fstab:
```
gksudo gedit /etc/fstab
```

Remount and change the swap partition:
```
sudo mount -a
free -m
```

---

### Post by S0m3th1ngw13rd on 2009-02-08
tried all that but I think I'm missing something.
here is result of sudo blkid

```
username@username-desktop:~$ sudo blkid
/dev/sda1: UUID="55b079f2-f28a-45a1-83ab-dc6d69a2bb49" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="719df0b5-116b-43c3-a147-41116321afaa" 
/dev/sdb1: UUID="127CCA8A7CCA67D5" LABEL="MICRO$HAFT WINDOZE" TYPE="ntfs" 
/dev/sdb5: UUID="82bfe797-b2a5-499a-9e32-0f0f78e86630" TYPE="swap" 
/dev/sda3: LABEL="HOME" UUID="5c746c3c-724e-4b08-ad3e-e47313f7db56" SEC_TYPE="ext2" TYPE="ext3" 
```

 here is fstab after changing UUID:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=55b079f2-f28a-45a1-83ab-dc6d69a2bb49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=719df0b5-116b-43c3-a147-41116321afaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

When i use  sudo mount -a /dev/sda5 result is
```
mount point none does not exist
```

---

### Post by caljohnsmith on 2009-02-08
How about:
```
sudo mkswap -U 719df0b5-116b-43c3-a147-41116321afaa /dev/sda5
```
Reboot, and you should be in business.

---

### Post by S0m3th1ngw13rd on 2009-02-08
> **caljohnsmith said:**
> How about:
```
sudo mkswap -U 719df0b5-116b-43c3-a147-41116321afaa /dev/sda5
```
Reboot, and you should be in business.

That did the trick thank you

---

### Post by Jarkycat on 2009-02-25
Just wanted to say 'thanks' to everyone for the information in this thread.  I too had issues with my swap partition (after using gparted to copy over to a new hard drive) and these posts solved the issue.

:)

---

