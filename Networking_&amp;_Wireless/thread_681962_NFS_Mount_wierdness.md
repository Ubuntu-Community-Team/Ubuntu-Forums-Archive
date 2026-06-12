---
title: "NFS Mount wierdness"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by Wayne Crouch on 2008-01-29
I have a Ubuntu 7.1 AMD_64 Desktop system (base) partitioned as follows :
---------------------------------------------------------------------------------------
# <file system> <mount point>    <type>      <options>			<dump>  <pass>
proc            /proc            proc	     defaults			0       0
/dev/sda1	/                ext3	     defaults,errors=remount-ro 0       1
/dev/sda2	/home            ext3	     defaults			0       2
/dev/sda3	none             swap	     sw				0       0
/dev/sda5	/nodes/nfs/node1 ext3	     defaults			0       2
/dev/sda6	/nodes/nfs/node2 ext3	     defaults			0       2
/dev/sda7	/nodes/nfs/node3 ext3	     defaults			0       2
/dev/scd0       /media/cdrom0	 udf,iso9660 user,noauto,exec		0       0
---------------------------------------------------------------------------------------
Note that sda4 is an extended partition, encompassing sda5..sda7, as required to meet
the PC standard limit of only four primary partitions. This was done with QParted,
when building base.

Base appears to be fully functional & I can access all partitions locally.

However, I also use base to provide network boot services (DHCP, TFTP. PXE, NFS)
for several other systems (node1, node2, node3) running Ubuntu 7.1 AMD_64
Server. They appear, at first glance, to boot successfully. But, rather
mysteriously, they all mount the same partition as root. That causes problems
in that such things as hostname are saved as files in /etc. So, with all three
using the same physical partition for root, the last one to change a file wins
on the next boot!

I first assumed this was a boot issue, possibly some interaction between
the various boot services. So, I checked the various configuration files
several times. They appear OK. In particular, each node has a unique file
(based on MAC address) in directory base:/tftpboot/pxelinux.cfg/, and these
files each define a unique nfsroot= parameter, as follows :
---------------------------------------------------------------------------------------
ls /tftpboot/pxelinux.cfg/
# .............................................................................
01-00-19-db-d1-c7-b3  01-00-19-db-d1-c7-c2  01-00-19-db-d1-c7-d8
# .............................................................................
cat /tftpboot/pxelinux.cfg/*
# .............................................................................
01-00-19-db-d1-c7-b3:
default linux
label linux
kernel vmlinuz-2.6.22-14-server
append initrd=initrd.img-2.6.22-14-server nfsroot=192.168.2.1:/nodes/nfs/node3
# .............................................................................
01-00-19-db-d1-c7-c2:
default linux
label linux
kernel vmlinuz-2.6.22-14-server
append initrd=initrd.img-2.6.22-14-server nfsroot=192.168.2.1:/nodes/nfs/node2
# .............................................................................
01-00-19-db-d1-c7-d8:
default linux
label linux
kernel vmlinuz-2.6.22-14-server
append initrd=initrd.img-2.6.22-14-server nfsroot=192.168.2.1:/nodes/nfs/node1
---------------------------------------------------------------------------------------


While trying to trace this down, I attempted some "local" NFS mounts on base,
in an attempt to isolate boot from network issues.
---------------------------------------------------------------------------------------
	# Make filesystems distinct
	(cd /nodes/nfs/node1 ; touch znode1)
	(cd /nodes/nfs/node2 ; touch znode2)
	(cd /nodes/nfs/node3 ; touch znode3)
	# Make auxillary mount points
	mkdir /xxx /xxx/node1 /xxx/node2 /xxx/node3
---------------------------------------------------------------------------------------
My /etc/exports exports the partition filesystems as follows :
---------------------------------------------------------------------------------------
/nodes/nfs	      192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node1 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node2 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node3 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
--------------------------------------------------------------------------------------------------------------------------------
ls /nodes/nfs/node1 /nodes/nfs/node2 /nodes/nfs/node3 ; # These are "hard" mounted via fstab & and are CORRECT
/nodes/nfs/node1:
bin   boot:  dev  home    initrd.img  lib64       media  opt   root  srv  test  usr  vmlinuz
boot  cdrom  etc  initrd  lib         lost+found  mnt    proc  sbin  sys  tmp   var  znode1

/nodes/nfs/node2:
bin   cdrom  etc   initrd      lib    lost+found  mnt  proc  sbin  sys  usr  vmlinuz  x.2  x.4  znode2
boot  dev    home  initrd.img  lib64  media       opt  root  srv   tmp  var  x.1      x.3  x.5

/nodes/nfs/node3:
bin   cdrom  etc   initrd      lib    lost+found  mnt  proc  sbin  sys  usr  vmlinuz  x.2  x.4  x.6  x.8  x.A  x.C  x.E  znode3
boot  dev    home  initrd.img  lib64  media       opt  root  srv   tmp  var  x.1      x.3  x.5  x.7  x.9  x.B  x.D  x.F
--------------------------------------------------------------------------------------------------------------------------------
Now, I locally NFS mounted the "root" filesystems for node1..node3
	mount -t /nodes/nfs/node1  /x/node1
	mount -t /nodes/nfs/node2  /x/node2
	mount -t /nodes/nfs/node3  /x/node3
And, I find that "ls /xxx/node1", "ls /xxx/node2", and "ls /xxx/node3" all give the same
results, "znode1" + some files expected to be common to all three partitions, with
none of the unique files for node2 and node3. I would appear that even local NFS
mounts are all reporting no errors, but are actually mounting /nodes/nfs/node1,
instead of the mount "source" requested. This is shown below :
--------------------------------------------------------------------------------------------------------------------------------
ls /xxx/node1 /xxx/node2 /xxx/node3 ; # These are NFS mounted as above & are BOGUS
/xxx/node1:
bin   boot:  dev  home    initrd.img  lib64       media  opt   root  srv  test  usr  vmlinuz
boot  cdrom  etc  initrd  lib         lost+found  mnt    proc  sbin  sys  tmp   var  znode1

/xxx/node2:
bin   boot:  dev  home    initrd.img  lib64       media  opt   root  srv  test  usr  vmlinuz
boot  cdrom  etc  initrd  lib         lost+found  mnt    proc  sbin  sys  tmp   var  znode1

/xxx/node3:
bin   boot:  dev  home    initrd.img  lib64       media  opt   root  srv  test  usr  vmlinuz
boot  cdrom  etc  initrd  lib         lost+found  mnt    proc  sbin  sys  tmp   var  znode1
--------------------------------------------------------------------------------------------------------------------------------


This local behavior is the same that I see when booting the remote nodes, where NFS mounts
the root filesystem for all three nodes to partition sda5! So, it would appear that my problem
is not really a boot problem, but some sort of NFS mount issue.

I am going slowly nuts here, as this makes no sense at all to me. Does anyone have any clue as to
what might be behind this behavior? Something I am doing wrong? A Ubuntu bug? Evil alien warlocks
from planet Claathu?

---

### Post by Eiríkr on 2008-02-22
One thought -- since each node is apparently supposed to be getting its own NFS-served node folder, why not change /etc/exports so that each node folder is served *not* to the whole subnet, but *just* to the remote machine that needs it?

Instead of what you've got:
---------------------------------------------------------------------------------------
/nodes/nfs 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node1 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node2 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node3 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check
---------------------------------------------------------------------------------------

... does this work, at least for the remote boots?
---------------------------------------------------------------------------------------
/nodes/nfs 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node1 192.168.2.[replace with node1 IP](rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node2 192.168.2.[replace with node2 IP](rw,no_root_squash,sync,no_subtree_check)
/nodes/nfs/node3 192.168.2.[replace with node3 IP](rw,no_root_squash,sync,no_subtree_check
---------------------------------------------------------------------------------------

Also, regarding the local NFS mount test silliness, it looks like there's an extra space in your exports file, where "no_subtree_check" is showing up as "no_subtree_c heck" -- is that actually in your exports file, or was it a hiccup when posting your message?  (It looks like the Forums might have a lameness filter in place -- how tiresome, especially at a site like this where you're pretty much guaranteed to have folks posting spaceless config file entries... :-/ )

And do you get any nfsd listings in /var/log/syslog that might be relevant?

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-02-23
One other thought -- your local NFS mount test looks a touch funny on second look --

> 
--------------------------------------------------------------------------------------------------------------------------------
Now, I locally NFS mounted the "root" filesystems for node1..node3
	mount -t /nodes/nfs/node1  /x/node1
	mount -t /nodes/nfs/node2  /x/node2
	mount -t /nodes/nfs/node3  /x/node3


The [font=courier]mount -t[/font] option should be followed by the filesystem type, in this case [font=courier]nfs[/font].  I don't suppose adding this in gives you more the expected result?

Cheers,

Eiríkr

---

