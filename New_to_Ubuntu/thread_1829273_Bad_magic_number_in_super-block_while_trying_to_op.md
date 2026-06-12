---
title: "Bad magic number in super-block while trying to open /dev/sda1"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by blade4 on 2011-08-20
Hi everyone , here's me posting my first question on the forum : I looked up a few performance tweaks for ext4 filesystem and wanted to try them out . I tried to use this code as per the instructions :


 tune2fs -o journal_data_writeback /dev/sda1


 but the output I got was this :


tune2fs 1.41.11 (14-Mar-2010) 
tune2fs: Bad magic number in super-block while trying to open /dev/sda1 Couldn't find valid filesystem superblock. 


I looked this up and a few sites said that this was a pretty bad situation . I'm still a noob but I think this has something to do with my fstab so I'm pasting the file here :


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    discard,data=writeback,loop,errors=remount-ro,noatime,nodiratime 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0


Any help would be appreciated ....

---

### Post by gordintoronto on 2011-08-20
Do you really want to do that?

[http://manpages.ubuntu.com/manpages/karmic/man8/tune2fs.8.html:](http://manpages.ubuntu.com/manpages/karmic/man8/tune2fs.8.html:)
" journal_data_writeback
When  the  filesystem  is  mounted  with journalling
enabled,  data  may  be  written   into   the   main
filesystem  after its metadata has been committed to
the journal.  This may increase throughput, however,
it  may  allow  old  data to appear in files after a
crash and journal recovery."

---

