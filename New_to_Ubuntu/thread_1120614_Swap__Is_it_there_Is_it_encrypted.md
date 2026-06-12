---
title: "Swap : Is it there? Is it encrypted?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-09
How do I check whether 

1) I have an activated swap partition
2) It is functioning with encryption

Thank you!

Sorry, just saw this:

[http://ubuntuforums.org/showthread.php?t=1044589&highlight=test+swap](http://ubuntuforums.org/showthread.php?t=1044589&highlight=test+swap)

My output is:

> Filename				Type		Size	Used	Priority
/dev/mapper/cswap                       partition	3903784	0	-1




> free -m
             total       used       free     shared    buffers     cached
Mem:          1986        631       1354          0         28        198
-/+ buffers/cache:        403       1582
Swap:         3812          0       3812



> blkid
/dev/sda1: UUID="9143ef04-c761-4b31-a7d2-684bec057db6" TYPE="ext4" 
/dev/sda5: UUID="cec2575c-8f68-4bda-ac41-9e18de4a936c" TYPE="crypt_LUKS" 
/dev/sda6: UUID="8f048d4c-d97e-4aa4-a532-9785d28f57e4" TYPE="crypt_LUKS" 
/dev/sda7: UUID="0199c0a3-01de-4764-a419-79131caa85ae" TYPE="crypt_LUKS" 
/dev/sdb5: UUID="e5a359ee-f43f-4294-a089-14557f2408b2" TYPE="crypt_LUKS" 
/dev/mapper/sda5_crypt: UUID="294eaed0-62ea-4e45-9f87-c80cd287a811" TYPE="ext4" 
/dev/mapper/sda6_crypt: UUID="03baf5cd-3206-4f6a-9dd8-56650159c5c1" TYPE="ext4" 
/dev/mapper/sda7_crypt: UUID="be9724c3-bc67-409d-902d-b9139e5a6083" TYPE="ext4" 
/dev/mapper/sdb5_crypt: UUID="84ba0426-641e-4b1e-a39d-938d3490014f" TYPE="ext4" 


From my fstab:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda5_crypt /               ext4    relatime,errors=remount-ro 0       1
/dev/mapper/sda7_crypt /backup         ext4    relatime        0       2
# /boot was on /dev/sda1 during installation
UUID=9143ef04-c761-4b31-a7d2-684bec057db6 /boot           ext4    relatime        0       2
/dev/mapper/sdb5_crypt /home           ext4    relatime        0       2
/dev/mapper/sda6_crypt /opt            ext4    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cswap       none    swap    sw      0       0



> cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory


---

### Post by blackgr on 2009-04-09
> **yeehi said:**
> How do I check whether 

1) I have an activated swap partition
2) It is functioning with encryption

Thank you!

Sorry, just saw this:

[http://ubuntuforums.org/showthread.php?t=1044589&highlight=test+swap](http://ubuntuforums.org/showthread.php?t=1044589&highlight=test+swap)

```
free -m
```

---

### Post by yeehi on 2009-04-09
blackgr, from my free -m output, do you think my swap is working?

---

### Post by sdennie on 2009-04-09
It's there and it's encrypted.  ;)

---

### Post by yeehi on 2009-04-10
Good, and thank you!

By the way, by looking at that info, how can you tell that swap is there, functioning and encrypted?

---

### Post by ibuclaw on 2009-04-10
This line here:
> /dev/mapper/cswap none swap sw 0 0

Although, to ensure that is it working properly:
```
cat /proc/swaps
```
and you should get something like this outputted in the first column.
> 
**Filename**
/dev/mapper/cswap


And to doubly make sure:
```
cryptsetup status cswap
```
And that will return something like so:
> 
**/dev/mapper/cswap is active:**
 cipher:  aes-cbc-plain
 keysize: 256 bits
 device:  /dev/.static/dev/sda8
 offset:  0 sectors
 size:    6297417 sectors
 mode:    read/write


Regards
Iain

---

### Post by sdennie on 2009-04-10
tinivole beat me to it...

---

