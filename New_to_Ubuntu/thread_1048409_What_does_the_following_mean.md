---
title: "What does the following mean?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ljk on 2009-01-23
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

And

E: Could not open file /var/lib/dpkg/status - open (116 Stale NFS file handle)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Ubuntu 8.10. The internet is working,occasionally, (wireless) but Add/Remove and Synaptic deliver the above messages.

Help appreciated.

Regards & thanks.

---

### Post by gettinoriginal on 2009-01-23
Make sure that Add/Remove and Synaptic are closed, then open a terminal and copy/paste each (separately):

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ljk on 2009-01-24
Apologies for the  non-descriptive posting and many thanks.

The terminal response to "sudo dpkg --configure -a" was;

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: Stale NFS file handle
ubuntu@ubuntu:~$ 

I don't know if it is important but the Ubuntu 8.10 installation is on a USB stick (12 GB of 16 GB).

After creating the USB bootable drive & rebooting from it, everything worked well; even from this laptop on a wireless network. Now there are problems with Synaptic etc.

Again, many thanks.

---

### Post by gjoellee on 2009-01-24
You can only run one package manager at the same time. You already had one running, and that error came.

Updating your system, just having Synaptic open, or just basically  using APT or DPKG

---

### Post by ljk on 2009-01-25
Thanks.

I just booted Ubuntu and waited until internet connections were OK - I then went to System ->Administration ->Update Manager to turn off any automatic package management. Before I had a chance to do anything, the following message appeared;

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (116 Stale NFS file handle), E:The package lists or status file could not be parsed or opened.'

I can't see any way that multiple package managers were open or running at the same time so immediately after startup. If they were, how do I "kill" them? There was no icon in the top menu bar showing that a package manager was running.

I have no idea how to "report this bug" as the message quoted above requests.

Again, I thank you for trying to help but I feel trapped in a vicious circle in this matter.

Regards,

---

### Post by ljk on 2009-01-25
Thanks.

I just booted Ubuntu and waited until internet connections were OK - I then went to System ->Administration ->Update Manager to turn off any automatic package management. Before I had a chance to do anything, the following message appeared;

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (116 Stale NFS file handle), E:The package lists or status file could not be parsed or opened.'

I can't see any way that multiple package managers were open or running at the same time so immediately after startup. If they were, how do I "kill" them? There was no icon in the top menu bar showing that a package manager was running.

I have no idea how to "report this bug" as the message quoted above requests.

Again, I thank you for trying to help but I feel trapped in a vicious circle in this matter.

Regards,

---

### Post by sisco311 on 2009-01-25
try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

According to the error message the /var/lib/dpkg/status file is not readable. The system stores a backup of this file (/var/lib/dpkg/status-old).

The cp (copy) command should replace the faulty file with the backup.

---

### Post by ljk on 2009-01-25
> **sisco311 said:**
> try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

According to the error message the /var/lib/dpkg/status file is not readable. The system stores a backup of this file (/var/lib/dpkg/status-old).

The cp (copy) command should replace the faulty file with the backup.

Thanks. Results below.

ubuntu@ubuntu:~$ sudo cp /var/lib/dpkg/status
cp: missing destination file operand after `/var/lib/dpkg/status'
Try `cp --help' for more information.
ubuntu@ubuntu:~$ 

And,

Fetched 2365kB in 5s (461kB/s)                             
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (116 Stale NFS file handle)
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ 

the latter had many lines of text about "Ign" & "Get" but I believe the important part is the part quoted.

Many thanks for trying to help,

Regards.

---

### Post by sisco311 on 2009-01-25
> **ljk said:**
> Thanks. Results below.

ubuntu@ubuntu:~$ sudo cp /var/lib/dpkg/status
cp: missing destination file operand after `/var/lib/dpkg/status'
Try `cp --help' for more information.
ubuntu@ubuntu:~$ 

And,

Fetched 2365kB in 5s (461kB/s)                             
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (116 Stale NFS file handle)
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ 

the latter had many lines of text about "Ign" & "Get" but I believe the important part is the part quoted.

Many thanks for trying to help,

Regards.

Copy/Paste the command exactly:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by ljk on 2009-01-26
> **sisco311 said:**
> Copy/Paste the command exactly:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Terminal responded
ubuntu@ubuntu:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
cp: accessing `/var/lib/dpkg/status': Stale NFS file handle
ubuntu@ubuntu:~$ 

I very much appreciate your help - the package manager problem seems to be the main obstacle to using Ubuntu 8.10, at the moment. The puzzling part is that everything seemed OK until I ran Synaptic. I had downloaded language support files for Japanese and had the SCIM IME working. I also installed WINE from the Add/Remove item under "Applications" - these error messages began later so, presumably, things worked properly at first.

This is the second installation of 8.10 on a USB stick. The first ran into the same problems so I re-installed after checking nothing remained from the first try.

Regards,

---

### Post by sisco311 on 2009-01-26
I've googled the error message and I found this:
> Q. Why do I get the following error message sometimes?
	Stale NFS file handle

A. This type of error message is seen when a file or directory that was opened by an NFS client is removed, renamed, or replaced. 
   To fix this problem, the NFS file handles must be renegotiated.

It's a little odd.

Please post the output of:
```
mount
```
and
```
ls -al /var/lib/dpkg/status*
```

---

### Post by ljk on 2009-01-27
> **sisco311 said:**
> I've googled the error message and I found this:


It's a little odd.

Please post the output of:
```
mount
```
and
```
ls -al /var/lib/dpkg/status*
```

Both outputs are attached. Unfortunately, I will not be able to respond to any messages until Monday.

Thanks again & apologies for all the work you're doing to help me.

Regards,

---

### Post by ljk on 2009-01-27
OOPs! Sorry. The atachments have not appeared with my last message. Below is the output (copied & pasted) of the terminal command "mount" - sorry it's so long.

"ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ "

And for "ls etc."

"ubuntu@ubuntu:~$ ls -al /var/lib/dpkg/status*
ls: cannot access /var/lib/dpkg/status: Stale NFS file handle
-rw-r--r-- 1 root root 1261845 2009-01-19 14:47 /var/lib/dpkg/status-old
ubuntu@ubuntu:~$ "

Many thanks and apologies for the un-attachments.

Regards,

---

### Post by zielgruppe on 2009-01-27
Hi, had the same problem. I have no idea why NFS is mentioned in the error message, but I just moved some files to make it working again. I did in the recovery root shell, maybe it works in normal gnome as well. Just move the /var/lib/dpkg to /var/lib/dpkg.old. Then copy it again, which might give you the usual error message (I just canceled it). You need some more files to copy (the folder *updates* and the file *status*), and that's it. Most probably not a clean solution, though.

---

### Post by ljk on 2009-02-02
Thanks & sorry for the delay in replying. Having problems with "multiquote" so comments are below.

> **zielgruppe said:**
> Hi, had the same problem. I have no idea why NFS is mentioned in the error message, but I just moved some files to make it working again. I did in the recovery root shell, maybe it works in normal gnome as well. 

 Just move the /var/lib/dpkg to /var/lib/dpkg.old. Then copy it again, which might give you the usual error message (I just canceled it).

 You need some more files to copy (the folder *updates* and the file *status*), and that's it.

Most probably not a clean solution, though.


  Again, sorry. I don't have any idea what "recovery root shell" is or how to use it.

  How do you just move it? Is it "drag & drop" or some terminal command?


  I'm totally lost now. Where are, (the folder *updates* and the file *status*), and where do I copy them to?

   Apologies for being so ignorant.


Any solution, clean or otherwise, would be most welcome. I thank you for your help.

Regards,

---

### Post by ljk on 2009-02-08
Hello.

I never managed to get the "stale file handles" sorted out, despite the kind advice I received on these forums.

I have now deleted the Ubuntu installations on 2 USB "thumb" drives and re-installed from scratch.

Everything seems to be working OK & I suspect the problem may have been caused because I didn't realize that the terminal window which appears as a drop-down item when the package manager is "installing dependecies" needs to have a number (from 1 - 4) entered to select an email configuration.

This is all very mystifying but entering 1 (no configuration) and hitting the Enter or Return key seemed to work.

I'll use the package managers with extreme caution from now on.

Many thanks to all who tried to help.

Best Regards.

---

### Post by zielgruppe on 2009-02-11
> I'll use the package managers with extreme caution from now on.

Good Idea ;)

My workaround was actually a bad idea. I realized later that removing any dpkg files leaves your package manager in an inconsistent state, which in the end breaks your systems even more...

---

