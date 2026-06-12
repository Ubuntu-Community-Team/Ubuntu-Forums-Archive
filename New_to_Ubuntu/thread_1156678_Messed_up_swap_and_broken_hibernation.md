---
title: "Messed up swap and broken hibernation"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by soyuz_one on 2009-05-12
Hi guys

A few months ago I tinkered around with making a swapfile as I was doing some numerical work and needed the extra memory. Anyway I think I ended up breaking my swap with the most obvious consequence to me being no hibernation. I've searched the forum for posts relating to this like making sure the UUID's match and turning swap on but I can't figure it out. ANy help would be appreciated.

I've included free, blkid, and my fstab below. 

             total       used       free     shared    buffers     cached
Mem:       2034016    1957452      76564          0     186652    1297468
-/+ buffers/cache:     473332    1560684
Swap:            0          0          0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         610     4895744   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         610        9230    69235712    7  HPFS/NTFS
/dev/sda3            9231       12034    22523130   83  Linux
/dev/sda4           12035       12161     1020127+   5  Extended
/dev/sda5           12035       12161     1020096   82  Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f407ac87-f9cd-4a12-9edc-b2db9886f950 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3bbe9fa9-3e85-400f-b563-7c4a76ea0e6f none            swap    sw              0       0
/dev/sda5 none            swap    sw              0       0
/swapfile swap swap defaults 0 0

---

### Post by Didius Falco on 2009-05-12
> **soyuz_one said:**
> Hi guys

A few months ago I tinkered around with making a swapfile as I was doing some numerical work and needed the extra memory. Anyway I think I ended up breaking my swap with the most obvious consequence to me being no hibernation. I've searched the forum for posts relating to this like making sure the UUID's match and turning swap on but I can't figure it out. ANy help would be appreciated.

I've included free, blkid, and my fstab below. 

             total       used       free     shared    buffers     cached
Mem:       2034016    1957452      76564          0     186652    1297468
-/+ buffers/cache:     473332    1560684
Swap:            0          0          0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         610     4895744   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         610        9230    69235712    7  HPFS/NTFS
/dev/sda3            9231       12034    22523130   83  Linux
/dev/sda4           12035       12161     1020127+   5  Extended
/dev/sda5           12035       12161     1020096   82  Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f407ac87-f9cd-4a12-9edc-b2db9886f950 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3bbe9fa9-3e85-400f-b563-7c4a76ea0e6f none            swap    sw              0       0
/dev/sda5 none            swap    sw              0       0
/swapfile swap swap defaults 0 0

Actually, you included ```
fdisk -l
``` and not ```
blkid
```

1. run blkid and confirm that the UUID number matches.

2. change this: ```
# /dev/sda5
UUID=3bbe9fa9-3e85-400f-b563-7c4a76ea0e6f none            swap    sw              0       0
/dev/sda5 none            swap    sw              0       0
/swapfile swap swap defaults 0 0
```to this: ```
# /dev/sda5
UUID=3bbe9fa9-3e85-400f-b563-7c4a76ea0e6f none            swap    sw              0       0
```

3. Reboot.

That should sort you out.

Regards,

Didius

---

