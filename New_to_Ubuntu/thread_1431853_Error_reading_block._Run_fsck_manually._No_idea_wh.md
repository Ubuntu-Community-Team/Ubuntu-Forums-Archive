---
title: "Error reading block. Run fsck manually. No idea what to do!"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Saraslife on 2010-03-17
A few days ago I was told to update my computer. After the update it told me to restart. As it was restarting it needed to do the routine drive check. So I waited for it to finish but it gave me this instead. 

error reading block 12877911 (attempt to read block from file system resulted in short read) while getting next inode from scan.
mountall: /dev/sda1: fsc/[419] terminated with status 4
mountall: file system has errors:/
Unit: mountall main process (411) terminated with status 3 
mount of file system failed
A maintenace shell will now be started.
Control D will terminate this shell and retry
root@sarahlinux:~#

Im running the newest version of ubuntu. I also have dual boot windows 7. Windows 7 wont start either. Ubuntu was installed first. 

Thanks!

---

### Post by ajgreeny on 2010-03-17
Boot to the Live CD, ensure none of your hard disk partitions are mounted and then in terminal run ```
sudo fsck /dev/sda1
```
Report back here any error messages it throws back at you, but hopefully that may solve the problem for you.

---

### Post by Saraslife on 2010-03-17
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 12877911 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes


Error reading block 12877912 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 12877913 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (3220736): Can't read next inode
e2fsck: aborted
ubuntu@ubuntu:~$

---

### Post by Saraslife on 2010-03-17
I Typed: sudo fsck -y /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 12976554 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976555 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976556 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976557 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976558 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976559 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976560 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976561 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976562 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976563 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976564 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976565 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976566 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976567 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976568 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 12976569 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 357200/4792320 files (2.0% non-contiguous), 2826891/19161520 blocks


Hope this works!

---

### Post by Saraslife on 2010-03-17
It worked! Thank you!

---

### Post by ajgreeny on 2010-03-17
I'm very glad it worked, but think you should keep a careful eye on things, and also ensure you have up to date backups of everything, just in case it is your hard disk that is beginning to show signs of failure.  Clonezilla perhaps?

If it were mine, I would also be slightly tempted to do a complete backup and format, and then a clean reinstall, though with a new version coming out in 5 weeks, it's perhaps worth carrying on till then as you are, backed up, of course, and then do a clean install of the new 10.04 in April.

---

### Post by audiomick on 2010-03-17
> **ajgreeny said:**
> I'm very glad it worked, but think you should keep a careful eye on things, and also ensure you have up to date backups of everything, just in case it is your hard disk that is beginning to show signs of failure.  Clonezilla perhaps?

If it were mine, I would also be slightly tempted to do a complete backup and format, and then a clean reinstall, though with a new version coming out in 5 weeks, it's perhaps worth carrying on till then as you are, backed up, of course, and then do a clean install of the new 10.04 in April.
Once again good advice from AJGreeny. (how does he do it?? );)

There is a thing called smartmontools that gives you good information about  the state of your drive. Good to know before you go to the trouble of re-installing.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by srs5694 on 2010-03-17
If you're using Ubuntu 9.10, try installing (if necessary) and using the gsmartcontrol program. This will give you easy access to your hard drives' built-in error monitoring systems, so that you can see if there are problems developing. On pre-9.10 versions of Ubunto, gsmartcontrol isn't available as a standard package, so you may need to either hunt it down elsewhere (I'm afraid I don't have any pointers handy) or use something else, such as the text-mode smartctl program (part of the smartmontools package).

---

### Post by audiomick on 2010-03-17
> **srs5694 said:**
> If you're using Ubuntu 9.10, try installing (if necessary) and using the [COLOR=Red]gsmartcontrol program[/COLOR]..... such as the text-mode[COLOR=Red] smartctl program[/COLOR] (part of the smartmontools package).
These are all referred to on the page that I posted the link to.

---

### Post by roadrash on 2012-07-04
This worked for me too thank you.

---

