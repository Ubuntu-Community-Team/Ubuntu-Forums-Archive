---
title: "Old Harddrive"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by timbob1957 on 2009-04-07
I have an old harddrive out of a old laptop...I have a case for it..and it will run off of usb cable...it works on my desktop which is win xp....but i cant get ubuntu to reconize it...any suggestions...

---

### Post by skymera on 2009-04-07
Hello :)

Can you open the terminal and post the output of

```
 sudo fdisk -l 
```

Please, note: That is a lower case  L

---

### Post by timbob1957 on 2009-04-07
sudo fdisk l.....then what?

---

### Post by RetchingRabbit on 2009-04-07
> **timbob1957 said:**
> sudo fdisk l.....then what?

"and post the output of"....sudo fdisk -l

---

### Post by timbob1957 on 2009-04-07
Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c1a5c1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4         460     3670852+  83  Linux
tim@tim:~$

---

### Post by the.phantom on 2009-04-07
some reason he started a new topic?

here is his reply

[http://ubuntuforums.org/showthread.php?t=1119272](http://ubuntuforums.org/showthread.php?t=1119272)

---

### Post by JohnLM_the_Ghost on 2009-04-07
hmm... ok... is there anything wrong with it?

---

### Post by the.phantom on 2009-04-07
his post is here

[http://ubuntuforums.org/showthread.php?t=1119210](http://ubuntuforums.org/showthread.php?t=1119210)

---

### Post by Rocket2DMn on 2009-04-07
Threads merged.

---

### Post by timbob1957 on 2009-04-07
nothing wrong as i can see....it works fine on my win xp desktop

---

### Post by louieb on 2009-04-07
No good reason for Ubuntu not to see the external drive. 
How old is the Ubuntu PC? Could be its USB ports are not working or the PC has USB 1.1 and the caddy is USB 2.0.

---

### Post by egalvan on 2009-04-08
The old drive is probalbly NTFS.

Depending on the version of Ubuntu, you may need to install ntfs-config to see NTFS drives.

---

