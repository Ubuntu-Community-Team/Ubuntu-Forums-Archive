---
title: "installing on clean hard drive and GRUBOS"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by drop bear on 2010-05-06
G'day from sunny South Australia (it's raining) and thanks for the welcome. 


The problem:  Just installed Linuxl (Mint) on my sister's geriatric HP. --YES, MY QUESTION IS ABOUT UBUNTU 


When I booted it I got a GRUB error;out of disc space.I had  never heard of GRUB. 

I did not manually partition the hard drive. Should I have? I don't know how. 

Is the error message because I did something wrong or because it's an old machine? 

A friend has suggested I install the latest Ubuntu.Would I need to partition the hard drive?  

I would greatly appreciate being pointed to a simple tutorial.

---

### Post by Peter09 on 2010-05-06
Mint is a flavour of Ubuntu so your o.k here.
 
When you installed Mint how much disk space did you allocate in the Partition dialog?
 
If your sister has no data on the machine that she wants to keep the you should select 'use the whole disk'.
 
Do you know how big the hard disk is on the system, and how much RAM it has?
 
 It may be you will need to go with Lbuntu (I think thats what its called). This requires less system resources.

---

### Post by jbrown96 on 2010-05-06
A strange problem. 
When your computer boots, hold the shift key. Choose the first entry that is marked "recovery." You shoul get a menu (blue, gray, and red), then choose root shell. At the command prompt type ```
mount -l
``` and post the output here. I don't need all of just lines that start with /dev/ and you can leave out the rest of the line past "type." Here's mine > /dev/md0 on / type ext4 (rw) [Fedora-12-i686-L]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
/dev/dm-0 on /media/lvm type ext4 (rw,noatime,nobarrier)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
 but I would only need > /dev/md0 /
/dev/dm-0 /media/lvm then also run ```
df -h
``` and post all the output.

---

