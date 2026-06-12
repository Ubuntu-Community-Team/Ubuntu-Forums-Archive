---
title: "Sharing HFS+ partition with nfs-kernel-server"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by calum on 2007-01-03
Is anyone successfully doing this, i.e. sharing out an HFS+ partition with nfs-kernel-server?  I just get a "Permission denied" error at the client side when I try to mount it, whether on the local machine or from a remote one.  I can share out an ext3 filesystem just fine.

The HFS+ share also works perfectly when I use nfs-user-server instead (on Edgy x86), but the user-server has a 2Gb file size restriction that makes it practically useless for me.  Is there a known breakage wrt to the HFS+ filesystem and the kernel-server?  If so, is there any way to get around the 2Gb limitation?

---

### Post by calum on 2007-01-03
If it's any help, strace output from mountd seems to pinpoint the problem area:

```

open("/proc/fs/nfsd/filehandle", O_RDWR) = 10
fstat64(10, {st_mode=S_IFREG|0600, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fbd000
write(10, "192.168.1.0/255.255.255.0 /media"..., 47) = -1 EPERM (Operation not permitted)
read(10, "", 4096)                      = 0
close(10) 

```

i.e. looks like it's trying to write to /proc/fs/nfsd/filehandle, and failing.

---

### Post by eecharlie on 2007-03-31
Well you're my hero for at least exposing the problem, I've been banging my head on this for days trying to figure out why I couldn't get it to work. I'm happy to live with the 2gb limit for now...

As a little token of usefulness to anyone else who comes across this, here's a little bash script for killing all the Finder/Spotlight hidden files that probably have stupid permissions:

#!/bin/bash
echo 'Recursively removing the following files/directories from' $PWD
for X in 'Desktop\ DB' 'Desktop\ DF' '.Spotlight*' '.TemporaryItems' '.Trashes' '.DS_Store'
do
        echo $X
        find -name "$X" -delete
done


Note that it doesn't need an argument, it just starts deleting from wherever you are, so be careful. Save as cleanUpFinderFiles.sh and run with  sh cleanUpFinderFiles.sh

---

