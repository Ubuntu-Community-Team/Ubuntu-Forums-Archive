---
title: "help getting second cd-rom working"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by alecwh on 2009-03-16
Hello,

I have two DVD drives in my desktop computer. One (cdrom0) can write DVDs, and the other (cdrom1) only reads them. The only problem is, lately, when I put a DVD or CD in cdrom1, the CD doesn't seem to mount. Navigating to /media/cdrom1/ only shows a blank browser.

Here is the relevant output of 'sudo lshw':

```
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8164B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0L06
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1

```

Can someone help me debug this? When I put a disc in cdrom0, an icon appears on my desktop, but this doesn't happen with cdrom1.

---

### Post by psychomichael on 2009-03-20
I'm having the same problem. The first combo drive works fine as long as I don't hook up the new combo drive. When I have them linked together neither works. Both drives are set to Cable Select. 

I made the directory for the second drive but I can't even find any info for the fstab.

---

