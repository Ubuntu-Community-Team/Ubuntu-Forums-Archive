---
title: "Mirroring on NAS without ssh"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by massimo.cristofoli on 2014-01-31
Hi everyone!

I have a Lacie Network Space 2 NAS connected to my router at home. The NAS partitions are mounted on my PC during boot via fstab.
At the moment, I access my NAS data mainly from LAN using the mounted partitions; sometimes from internet using FTP.

I wuold like to change the acces mode a little: 
- mount some partitions in this way, allowing data access from the LAN
- copy the full content of some other partitions to my PC, and sometimes sync the data with the NAS 
- the data will be mirrored only from PC to NAS (no sync from NAS to PC)
- I DON'T want to backup data (with versions, compressed formats, ...), but to have a copy of them, so I can access them from other PCs

My idea is to use RSYNC, and I'm able to mirror my data if I work with the mounted partition. My idea is to remove the network partition, so I will work only on the data on my PC (without the risk to create files on the server instead of the local drive and screw the mirroring) and than sync the changes to NAS. The idea is to use RSYNC via ssh, but my NAS doesn't have ssh (well, I can hack it, but I prefer not to), and ssh connection obviously fails.

Is there any other method to do this thing? Backup softwares could be good if I can backup files as is (not compressed) and without backup versoning (every new backup must rewrite the last one, and files deleted from local drive must be deleted on the NAS).

Thanks!
MIX

---

### Post by TheFu on 2014-01-31
The limitation is on your router.  Which storage protocols does it support?

---

### Post by massimo.cristofoli on 2014-01-31
Uhm... I think you mean on the NAS, not on the router, right?
I don't find much informations about the protocols available on the Lacie Network Space 2. Only FTP is listed on the manual. SMB can also be used.
Side note, Apple Time Machine can be used with this NAS (info from the internet; didn't test it).

---

### Post by TheFu on 2014-01-31
> **massimo.cristofoli said:**
> Uhm... I think you mean on the NAS, not on the router, right?
I don't find much informations about the protocols available on the Lacie Network Space 2. Only FTP is listed on the manual. SMB can also be used.
Side note, Apple Time Machine can be used with this NAS (info from the internet; didn't test it).

Sorry. My mistake. I think of Lacie as expensive, high quality, external HDDs with Firewire. Perhaps that has changed.
According to this: [http://www.lacie.com/us/support/support_manifest.htm?id=10300&article=1208](http://www.lacie.com/us/support/support_manifest.htm?id=10300&article=1208) it supports NFS - looks like NFSv3 so IP addresses are the only authentication.  I can't tell which file systems are supported. Appears to be a Linux-based NAS, so EXT3 should be possible, if not EXT4, XFS, JFS, and other advanced options.

NFS support is what I would use. This will allow nearly complete file permissions control as though the storage were local to the remote machines.  CIFS is a distant 20th choice for NAS access, IMHO.
rsync will be used in a local-to-local way ... which can cause oddities during mirrors, since rsync will completely copy changed files instead of checking for similar blocks when it thinks the disks are local. These are just the defaults. There are ways around it.  I use timestamp and file size checks to avoid a complete copy, which is not 100%, but has been _good enough_ here. For really large files, like virtual machine images, zsync might be better. I backup VMs from inside, not outside. Find it 1000x more efficient.

I would avoid using FTP anywhere ... for any reason. The [liabilities]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") are just too many. Google will find 50 other, similar articles on this.

I just reread your posts - what is "PC"?  Are there other clients?  I've assumed PC = Linux machine above and that all other clients are also Linux based.  At not time would I allow the NAS to be accessed from the internet directly. Call me paranoid, but any device that can't be patched weekly and doesn't run a firewall has no business being accessed over the internet - **especially with a  non-secure protocol like FTP.**

---

### Post by massimo.cristofoli on 2014-01-31
Thanks for the detailed answer!

First, I try to clarify the "topology" of the network (that is quite simple). A little scheme

PC (notebook with Ubuntu) ------- ROUTER ----- NAS (Lacie Network Space 2)

Just this.
There are other PCs that will connect to the NAS, and they access to a shared partition (the one that I don't want to mirror, but just mount on my PC (with CIFS at the moment) when I'm home) and private partitions (accessed with username/password). My private partition is the one that I want to mirror (again, at the moment it's auto-mounted with CIFS).

I will make some tests for mounting with NFS (any hint about this? Like ftab configurations or something else).
Also, resuming the thread title, what to use for mirroring with NFS?

---

### Post by TheFu on 2014-01-31
rsync.
Google "ubuntu nfs" for the steps. The Lacie will need to be configured (probably though a web interface) for each NFS client machine and "exports."

Hopefully the network is really
```

WAN - router --- PC
             --- Lacie NAS
```
with both the PC and NAS on the same subnet.

---

### Post by massimo.cristofoli on 2014-01-31
> **TheFu said:**
> Hopefully the network is really
```

WAN - router --- PC
             --- Lacie NAS
```
with both the PC and NAS on the same subnet.

Indeed...
I'll start playing with NFS. Updates soon (I hope).

---

### Post by massimo.cristofoli on 2014-02-03
NFS seems to be hardly usable with this NAS. The document you linked, despite the top image, is related to another Lacie product.
I choose a different way: script that temporary mount the NAS partition with cifs, than calls rsync and pre-post backup commands, than unmount it. Seems the best solution with this NAS.
Other ideas are welcome!

---

### Post by TheFu on 2014-02-03
If all it supports is FTP or CIFS, then CIFS is the lessor of the evils and living with the lack of control over users/groups and file permissions will be something to work around.  rsync might not be the best "backup" method for anything other than pure data.

BTW, there is backup software that does versioning but also leaves the most recent backup as a mirror (like rsync).  **rdiff-backup** is the name. Never tried to use it to NTFS/CIFS-based storage.  Test it on something small, like the /etc/ directory to see what I mean. File permissions will be an issue, but "some backup" is better than no backup.  Anyway, I think you'll like it - but if the data stored is music or videos, I would use straight rsync. Versioning of large files sucks too much storage, but for stuff in ~/, it is fantastic!  If it doesn't do what you need, delete the target. Simple.

---

