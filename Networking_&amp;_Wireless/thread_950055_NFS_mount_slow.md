---
title: "NFS mount slow"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by pseudosig on 2008-10-16
I've been scouring the internet the last week and I haven't found a solution to my problem.  I have an NFS server that's connected to my router via ethernet.  My NFS client is is an xps 1530 laptop.  Sometimes, when I mount a directory onto my laptop, I get download/uplod rates around 3 megabytes / sec.  If I umount the directory, and remount it immediately after, often times I upload/download 300 kilobytes.  My speeds will usually stay consistent after mounting, but the consistency of each time I mount is nearly non-existent.

I'm not sure where to begin...

Here's my exports file:
/media/disk 192.168.1.1/24(rw,sync,no_root_squash,no_subtree_check)

And my mount command is:
sudo mount -t nfs media.local:/media/disk /mounts/Home\ Share/

I've tried so many different combinations of export/mount params.  This above are the ones I get the fastest download/upload with.

Though I think 3 megabytes is a bit slow NFS...

Any ideas?

---

### Post by pseudosig on 2008-10-17
Bumping this... no ideas then?

---

