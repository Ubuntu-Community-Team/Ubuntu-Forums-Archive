---
title: "Moving Partitions, problems?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-05-31
I've been changing my partitions around, and I figured out that my installation is on an extended partition with another encrypted partition. I really want everything to be on primary partitions, so I want to move them around. I know that I will need to re-install grub and update /etc/fstab, but is there is anything else I need to do?


Current layout:
/dev/sda1    Kubuntu (will be removed)
/dev/sda2    (Extended "container")
   /dev/sda5 Mandriva (this is what I want to move)
   /dev/sda6 Encrypted partition


What I want:
/dev/sda1  Mandriva
/dev/sda2  empty partition to try other distros
/dev/sda3  encrypted partition

Edit: I was going to use ```
sudo rsync -avz --exclude=/proc --exclude=/sys --exclude=/media / /media/new-root
``` will this work? Any other directories to exclude? Any other options that I should use to preserve links or permissions, etc?

Thanks

---

