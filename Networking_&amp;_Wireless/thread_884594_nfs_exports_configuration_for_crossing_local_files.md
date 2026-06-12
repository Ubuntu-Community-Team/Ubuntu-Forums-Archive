---
title: "nfs exports configuration for crossing local filesystems"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by tenzen on 2008-08-09
Hello all, 

I cant seem to find the right search terms to figure out how to do this so any help or direction pointing would be very helpful.

I have a ubuntu server 8.04 running on x64.    I have a ubuntu desktop 8.04 running on x32.

**On my server:**
I have an export (/data) that has 3 directories under it:
/data/os (directory on /dev/md0 mounted as / )
/data/storage (/dev/md1 mounted as /data/storage)
/data/striped (/dev/md2 mounted as /data/striped)

I have exported /data: 
/data 192.168.20.0/24(rw,async,no_root_squash,no_subtree_check

**On my Desktop:**
I have mounted /data using /etc/fstab:
192.168.20.10:/data     /media/server   nfs     rw,nfsvers=3    0       0

Now, This works except that my two mounted filesystems (storage and striped) show only the directories mounted in /.  For example:
From my desktop when I write to /media/server/storage it writes to /data/storage, but instead of writing to mounted device /dev/md1, it writes to root mounted device /dev/md0.

Any thoughts or is this a limitation of nfs?

Thanks

---

### Post by tenzen on 2008-08-09
Got it... found this post:

[http://blogs.sun.com/tdh/entry/how_nfsv4_should_work_when](http://blogs.sun.com/tdh/entry/how_nfsv4_should_work_when)


Essentially you have to export each of your seperate filesystems and then nfs will automount the others...

my new exports:
/data 192.168.20.0/24(rw,async,no_root_squash,crossmnt,no_subtree_check)
/data/striped 192.168.20.0/24(rw,async,no_root_squash,crossmnt,no_subtree_check)
/data/storage 192.168.20.0/24(rw,async,no_root_squash,crossmnt,no_subtree_check)

now it works fine.. 

Thanks all for looking

---

