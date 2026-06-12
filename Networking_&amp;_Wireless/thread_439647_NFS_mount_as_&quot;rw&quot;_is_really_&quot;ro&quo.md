---
title: "NFS mount as &quot;rw&quot; is really &quot;ro&quot; - Feisty &amp; ReadyNAS"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by owen_pg on 2007-05-10
I have NFS mounts set up on the 64 bit Feisty client to exports from an Infrant ReadyNAS NV+ nas device.

My /etc/fstab has lines like:

192.168.20.130:/VMWare /mnt/VMWare nfs rw,users,rsize=4096,wsize=4096,hard

Just to be on the safe side, I have the same UID and GID as the owner of the share on the NAS device.

The "mount" command shows that it should be read-write access - but it isn't:
192.168.20.130:/VMWare on /mnt/VMWare type nfs (rw,rsize=4096,wsize=4096,hard,addr=192.168.20.130) 

owen@OwenKU704:/mnt/VMWare$ touch testfile
touch: cannot touch `testfile': Read-only file system

Now, I can mount this same share from a MAC OS 10.4.9 client as any user and have it writable.

The support suggestion from Infrant was that this may be a problem with the Ubuntu 2.6.20 kernel.  See here:
[http://lkml.org/lkml/2006/10/18/264](http://lkml.org/lkml/2006/10/18/264) 

and here:
[http://www.infrant.com/forum/viewtopic.php?p=56595#56595](http://www.infrant.com/forum/viewtopic.php?p=56595#56595)

On the basis that I can mount this share as writable from my MAC client I'd tend to agree.

Any comments (on what I could be doing wrong)?

Cheers,

Owen
;-)

---

### Post by docsmooth on 2007-05-11
I'm kinda new to NFS, but have you tried either async or nointr options?  Also, I've never seen an "address=" option in the NFS mount before - is that required in your situation?

When I've had those issues, it's been an option wrong on the NFS server.

---

### Post by owen_pg on 2007-05-12
Hi dozsmooth,

The entry in /etc/fstab doesn't have an address - that was shown as the result of the "mount" comand.

I think the answer is that the Infrant ReadyNAS, which uses a Linux kernel by the way, is now picked up by the Ubuntu client as having all the mount points on one partition and now assumes that there could be data corruption as more than one (i.e. nested) writable mount points exist on the same serving partition.  This makes sense according to this bug report:
[http://lkml.org/lkml/2006/10/18/264](http://lkml.org/lkml/2006/10/18/264)

Ho hum,

Owen

---

### Post by bluefox83 on 2007-05-12
I'm having a similar problem, but instead of mounting a NAS device I'm trying to write to a shared directory from a regular old feisty fawn client machine, it keeps giving me the same error though. that i don't have permission to write. and I haven't seen any info to help on this. but just to help with diagnoses. I'm going to post everything i can think of:

Server machine:

/etc/exports - 
/d2/Shared      192.168.1.3/255.255.255.0(rw,async,subtree_check)

/etc/hosts.allow-
portmap: 192.168.1.3

/etc/hosts.deny-
portmap mountd nfsd statd lockd rquoted : ALL

File permissions for /d2/Shared -
drwxr-xr-x  2 bluefox bluefox  4096 2007-05-12 21:43 Shared

Client Machine:

/etc/fstab -
192.168.1.5:/d2/Shared /home/beth/Shared nfs rsize=8192,wsize=8192,timeo=14,intr



Now when I mount the shared folder i don't get any errors at all. It's when i try to write to the shared directory that i have trouble...

bluefox@bethubuntu:/home/beth/Shared$ mkdir test
mkdir: cannot create directory `test': Permission denied


I get the same error when I try using sudo as well.

---

