---
title: "mount: wrong fs type, bad option, bad superblock"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by guarriman on 2007-12-12
Hi.

Using Ubuntu 7.10 I want to mount a directory shared on a Fedora machine with NFS.

On Fedora machine (fedoraserver):
* edited '/etc/exports' and added:
-----------
/home/mydir/       pc09(rw)
-----------
* /etc/rc.d/init.d/nfs restart

On Ubuntu machine (pc09)
* mkdir /home/john/server-mydir
* mount -o nfsvers=2 fedoraserver:/home/mydir /home/jonh/server-mydir -o nfsvers=2

But I get this error message:
-------
mount: wrong fs type, bad option, bad superblock on fedoraserver:/home/mydir/,
       missing codepage or helper program, or other error
-------

'fedoraserver' does exist for 'pc09' and 'pc09' does exist for 'fedoraserver'. What am I doing wrong?

Thank you very much.

---

### Post by beorn! on 2007-12-12
Just a quick thought... try replacing the PC09 with the IP address of the client machine in your /etc/exports...

also how are you sharing the directory... over wan, lan? if a basic lan maybe 192.168*.* would suffice...

mine looks like...

/media/Tolstoy  *.*.*.*(rw,no_root_squash,async)

---

### Post by guarriman on 2007-12-12
Hi beorn. Thank you very much for you answer.

I tried with:
```

[]# mount -o nfsvers=2 192.168.2.3:/home/mydir /home/jonh/server-mydir -t nfs

```
and changed "/home/mydir/ pc09(rw)" with "/home/mydir/ 192.168.2.109(rw)"

but got the same error message :(

I'm using a LAN

---

### Post by beorn! on 2007-12-13
Sounds like it is actually the fedora box, then.

Recheck the following files
/etc/exports
/etc/hosts.allow
/etc/hosts.deny
/etc/sysconfig/nfs

The following tutorial is pretty thorough. 

[http://fconfig.wordpress.com/2006/08/17/setting-up-a-fedora-nfs-server/](http://fconfig.wordpress.com/2006/08/17/setting-up-a-fedora-nfs-server/)

If at that point you are still having problems... Let me know, I'll fire up fedora on my virtual machine and walk you through it step by step.

Also... just a personal preference, but since I am the only person who uses my box, I set up all my nfs mounts in my fstab.... Is there a reason why you prefer to do it manually?

---

### Post by SonicSteve on 2007-12-13
I know that Using Samba for networking will give this message when you don't have SMBFS (samba file system) installed.
It could be that you need to install the file system package for NFS. It's just a thought, it may already be installed, I'm not sure.

---

### Post by tomboy on 2007-12-14
Try installing nfs-common and if that's not helping, install portmap too.


> **SonicSteve said:**
> I know that Using Samba for networking will give this message when you don't have SMBFS (samba file system) installed.
It could be that you need to install the file system package for NFS. It's just a thought, it may already be installed, I'm not sure.

---

### Post by beorn! on 2007-12-25
guarriman,

Did installing nfs-common solve your issue? If so, you should close this thread.

---

### Post by DigitalWarrior on 2007-12-26
I had the exact same problem and this solved it!  Thanks Ubuntuforums, you rock!

DW

---

### Post by eric70x7 on 2007-12-30
I had this problem after upgrading from Feisty to Gutsy.  Don't know why nfs-common got "uninstalled" in the process, but installing it fixed the problem.  Thanks!

---

### Post by beefcurry on 2008-01-02
Yup looks like its pretty common, upgrading to Gutsy uhninstalled me nfs-common package as well.

---

### Post by dogeatery on 2008-01-03
Hi, I have just had this VERY same problem in Gutsy (I just upgraded a couple days ago) concerning my SD card reader.  It gives me the EXACT same error message and details and will not mount my card.  Here is the output for dmesg|tail:

dogeatery@dogeatery:~$ dmesg|tail
[ 2567.920000] sdb: assuming drive cache: write through
[ 2567.920000] SCSI device sdb: 4022272 512-byte hdwr sectors (2059 MB)
[ 2567.924000] sdb: Write Protect is off
[ 2567.924000] sdb: Mode Sense: 03 00 00 00
[ 2567.924000] sdb: assuming drive cache: write through
[ 2567.924000]  sdb: sdb1
[ 2567.924000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 2567.924000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2570.116000] FAT: Unrecognized mount option "usefree" or missing value
[ 2602.364000] FAT: Unrecognized mount option "usefree" or missing value

I tried installing nfs-common and there has been no change.  Any other ideas?

---

### Post by dogeatery on 2008-01-03
Okay, did some more thorough digging on this forum and found [this]("http://pysdm.sourceforge.net/")
and this [http://ubuntuforums.org/showthread.php?t=582045&highlight=gutsy+usb+mount+problem&page=6](http://ubuntuforums.org/showthread.php?t=582045&highlight=gutsy+usb+mount+problem&page=6)

sudo aptitude install pysdm

then sudo pysdm

then double click on the left menu to open your device (it must be plugged in, then click refresh)  You can set all the options you want with it and then it should work just fine.  Good luck to anyone else with this problem.

---

### Post by jhipkiss on 2008-01-07
Yes, me too, this solved it for me too.

Thanks

Jonathan


> **eric70x7 said:**
> I had this problem after upgrading from Feisty to Gutsy.  Don't know why nfs-common got "uninstalled" in the process, but installing it fixed the problem.  Thanks!

---

### Post by rgeddes on 2008-05-22
I set up nfs on a server:

sudo apt-get install nfs-kernel-server

and setup the export file on the server
-------------------
on the client I executed

sudo mount <nfs-server-name>:<source dir> <target dir> -t nfs

and I kept getting the same error message as listed on this thread. 

I read some of the other comments about how nfs-common being lost during upgrades.  Well, I checked on the server... it was there.  I realized that the comments made no mention of nfs-common being on the client or server.

I installed nfs-common on the **client** and nfs works correctly.

The one thing I noticed is that a server was started on my client box... the portmap daemon listening on tcp port 111.  

Question: is there a way for the client to run nfs without the portmap daemon?  I want to reduce the number of processes listening on my boxes as much as possible for security reasons.

---

