---
title: "Not enough free disk space for updates"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by jude700 on 2009-06-27
Went to d/l Ubuntu updates and got the following.  Am now d/l'ing groups at a time.  HDD is 70.1GB with 7.5 GB used & 62.5 GB free
Contents: 169,714 items, totalling 3.3 GB
(some contents unreadable)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Not enough free disk space

The upgrade needs a total of 355M free space on disk '/'. Please free at least an additional 258M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Restarted 



Not enough free disk space

The upgrade needs a total of 341M free space on disk '/'. Please free at least an additional 259M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With download size 78.oMB 

The upgrade needs a total of 331M free space on disk '/'. Please free at least an additional 253M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With download size 3.3 MB

Not enough free disk space

The upgrade needs a total of 66.4M free space on disk '/'. Please free at least an additional 834k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Restarted

With download size 983 kb


Not enough free disk space

The upgrade needs a total of 63.9M free space on disk '/'. Please free at least an additional 610k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Restarted

Version 2.26.1-0ubuntu2: 

  * debian/patches/90_upstream_change_fix_calendar_crasher.patch:
    - upstream change to fix a calendar crasher leading to evolution hanging
      (lp: #357636)

With download size 47 kb



Not enough free disk space

The upgrade needs a total of 63.0M free space on disk '/'. Please free at least an additional 1052k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With download size 47 kb



Not enough free disk space

The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 1060k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

jun 27 10:02

GVFS

Version 1.2.2-0ubuntu2: 

  * debian/patches/99_sftp_group_perm_check.patch: 
    - fixes a failure to check group permissions on sftp hosts (lp: #312396)

GVFS-Backends

Version 1.2.2-0ubuntu2: 

  * debian/patches/99_sftp_group_perm_check.patch: 
    - fixes a failure to check group permissions on sftp hosts (lp: #312396)

GVFS-bin

Version 1.2.2-0ubuntu2: 

  * debian/patches/99_sftp_group_perm_check.patch: 
    - fixes a failure to check group permissions on sftp hosts (lp: #312396)

GVFS-fuse

Version 1.2.2-0ubuntu2: 

  * debian/patches/99_sftp_group_perm_check.patch: 
    - fixes a failure to check group permissions on sftp hosts (lp: #312396)


With download size 983 kb

Not enough free disk space

The upgrade needs a total of 63.9M free space on disk '/'. Please free at least an additional 4931k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
Version 0.5.12~rc1+git20090403-0ubuntu3: 

  * 87_standalone_smbios.patch: Fix typos which caused Dell wifi killswitches
    to not work any more. (LP: #368553)


Version 0.5.12~rc1+git20090403-0ubuntu2: 

  * debian/patches/50_no_crash_on_md_blockdev.patch:
    - When adding a block device, don't assume that the parent 
      has storage capability. This fixes a crash where the device
      is re-parented to the root computer device object (such as
      with mdraid devices). LP: #361689. 


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With download size 386 kb

Version 0.5.12~rc1+git20090403-0ubuntu3: 

  * 87_standalone_smbios.patch: Fix typos which caused Dell wifi killswitches
    to not work any more. (LP: #368553)


Version 0.5.12~rc1+git20090403-0ubuntu2: 

  * debian/patches/50_no_crash_on_md_blockdev.patch:
    - When adding a block device, don't assume that the parent 
      has storage capability. This fixes a crash where the device
      is re-parented to the root computer device object (such as
      with mdraid devices). LP: #361689. 


Not enough free disk space

The upgrade needs a total of 63.3M free space on disk '/'. Please free at least an additional 7276k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With download size 41 kb

Version 4.32-0ubuntu4.1: 

  * debian/hid2hci.rules:
    - Update rule to work properly with newer version of udev. (LP: #330934)

Not enough free disk space

The upgrade needs a total of 63.0M free space on disk '/'. Please free at least an additional 40.6M of disk space on '[COLOR="Red"]/[/COLOR]'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

My question: Where is disk '[COLOR="Red"]/[/COLOR]'?  :confused:


Hope you had a good week and have a good week-end

---

### Post by cariboo on 2009-06-27
Open an Applications-->Accessories-->terminal and type:

```
sudo apt-get clean
```

This will remove all archived packages in /var/cache/apt/archives, and just to make sure there are no unsed dependencies, in the same terminal type:

```
sudo apt-get autoremove
```

Open nautilus (Places-->Home Folder), then click File System in the left pane. that is /, or in a terminal type:

```
cd /
```

To find how much of your partitions are used in the same terminal type:

```
df -h
```

You should get a listing that looks something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.5G  4.1G  1.2G  79% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  324K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
/dev/sda2             108G   61G   42G  60% /home
/dev/sda4             113G   41G   68G  38% /home/storage
```

Note that /dev/sda1 = / in my case, and I have 1.2Gb free

---

### Post by MasterProg on 2009-06-27
Try running 'sudo apt-get clean' as update manager suggests and install the updates again.

The disk '/' is the root. It is the disk where you have Ubuntu installed.

---

### Post by philcamlin on 2009-06-27
empty your trash ?

---

### Post by MasterProg on 2009-06-27
Yeah, and delete your old and/or unnecessary files. ;)

---

### Post by graabein on 2009-06-30
I have the same problem. I did apt-get clean and autoremove and trimmed it down a bit but there's still not enough free space. 

I'm running LXDE/Openbox so I don't know how to open trash?

Is there no way I can configure update-manager to use another partition while upgrading?

---

### Post by mwcrowley on 2009-06-30
Your best bet is to move your largest files to another partition.

---

### Post by raymondh on 2009-06-30
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by graabein on 2009-07-01
> **mwcrowley said:**
> Your best bet is to move your largest files to another partition.

I have emptied the trash and I did a search for files over 500M but none resided on '/'. Deleting files from /home directory won't help since home is mapped to another partition?

```
$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.6G  3.5G  954M  79% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  120K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M     0  252M   0% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda3              68G   53G   13G  81% /home

```

Update Manager says I have to free up 278M of space before upgrading... 

What I really need is a new computer but I keep postponing it since I rarely use it.

I tried removing the GIMP, Abiword and Open Office but it wouldn't let me remove the latter two. How come?

---

### Post by halitech on 2009-07-01
possible option is to use the live cd and shrink the /home partition and give the space to the / partition, although space there is limited as well but might help.

---

### Post by Flimm on 2009-07-01
Use Applications, Accessories, Disk Usage Analyser (Baobab) to find large files that you might want to delete.

---

### Post by graabein on 2009-07-01
Good idea halitech. I was thinking of using gparted to increase root partition size but not sure if it would work. A live CD is probably the way to do it. I'll try it when I find the time. Thanks everyone!

---

