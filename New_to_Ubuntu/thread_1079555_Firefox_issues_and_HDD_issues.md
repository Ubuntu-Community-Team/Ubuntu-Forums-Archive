---
title: "Firefox issues and HDD issues"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by iminhell on 2009-02-24
First off Firefox is being stubborn. Clean install of 8.10. Bookmarks don't seem to work nor does the back button. I had messed with reinstalling FF and seemed to find a program that was in conflict. Well I guess it wasn't the fix because my lack of bookmarks and back button is back.
Far as Synaptic says I have the following installed,
Firefox, 3.0.6+nobinonly+OubuntuO8.10.1
ubufox, 0.6-Oubuntu1.8.10.1
firefox-3.0, 3.0.6+nobinonly+OubuntuO8.10.1
firefox-3.0-branding, 3.0.6+nobinonly+OubuntuO8.10.1

Any clue on a fix?



Also HDD space seems to be off. I have 90GB open and unused but don't seem to be able to use that space. Last night I was trying to download the Ubuntu Studio .iso to the desktop and it came up with a message basically saying that there was not enough room on the desktop for the 1.2 GB .iso. I encountered a similar problem while trying to rip a CD (some tmp folder). On my previous working install I had no issues with space and far as I know I did this install the same. So I'm at a loss as to what the problem is.
Help?




-John

---

### Post by taurus on 2009-02-24
Open a terminal and post the output of this command to see about your disk space.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by iminhell on 2009-02-24
[quote=df -h]Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      6.5G  6.1G     0 100% /
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  108K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.9M  978M   1% /dev
tmpfs                 981M  336K  981M   1% /dev/shm
/dev/sda2              87G  8.3G   79G  10% /host
lrm                   981M  2.0M  979M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M  156K  868K  16% /tmp
[/quote]





... and Firefox just quit on me. Closed on it's own :mad:
Seems to be Flash related. But I can't figure out what or why.

---

### Post by dannyboy79 on 2009-02-24
your root drive (/) is full!!

can you please show us the following commands

```
sudo fdisk -l
```

```
mount
```

```
cat /etc/fstab
```

---

### Post by taurus on 2009-02-24
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by iminhell on 2009-02-24
> **dannyboy79 said:**
> your root drive (/) is full!!

can you please show us the following commands

```
sudo fdisk -l
```


Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe3d82c47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13841   104631292    7  HPFS/NTFS
/dev/sda2           13841       25842    90726400    7  HPFS/NTFS


> **dannyboy79 said:**
> ```
mount
```


/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


> **dannyboy79 said:**
> ```
cat /etc/fstab
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  defaults                 0  0  
/host/ubuntu/disks/root.disk  /            ext3  loop,errors=remount-ro   0  1  
/host/ubuntu/disks/boot       /boot        none  bind                     0  0  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                  0  0  
/dev/sdg1                     /media/sdg1  ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sdb                      /media/sdb   ntfs  nls=iso8859-1,noauto     0  0  



> **taurus said:**
> ```
sudo apt-get clean
sudo apt-get autoremove


john@ubuntu:~$ sudo apt-get clean
john@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libstrigiqtdbusclient0 libclucene0ldbl libarts1c2a kdelibs4c2a
  libartsc0 libqt4-opengl libqt4-assistant amarok-engine-xine libgcj9-0
  ttf-wqy-zenhei libgcj-bc libxine1-x kdebase-runtime-data-common libqt4-test
  ttf-kannada-fonts libqt4-sql-mysql libqt4-dbus libxine1-misc-plugins
  kdelibs-data libxcb-xv0 phonon libqt4-qt3support amarok-common liblualib50
  python-qt4-common kde-icons-oxygen libxine1-bin ruby1.8 libqt4-xmlpatterns
  ttf-liberation libqt4-help python-qt4 ruby libqt4-webkit kdelibs5-data
  libqtcore4 libavahi-qt3-1 libgcj-common python-sip4 ttf-telugu-fonts
  libxcb-shape0 tzdata-java libgcj9-jar libqt4-sql libifp4 libqt4-svg
  phonon-backend-gstreamer libstreamanalyzer0 libphonon4 libqt4-xml
  libqt4-network libqt4-designer libxvmc1 libqtgui4 ttf-oriya-fonts libpq5
  libstreams0 libmodplug0c2 liblua50 libruby1.8 libqt4-script
  ttf-bengali-fonts libxcb-shm0 kdebase-runtime-data libnjb5 qt4-qtconfig
  libxine1-console libxine1
The following packages will be REMOVED:
  amarok-common amarok-engine-xine gcj-4.3-base kde-icons-oxygen
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-data kdelibs4c2a
  kdelibs5-data libarts1c2a libartsc0 libavahi-qt3-1 libclucene0ldbl libgcj-bc
  libgcj-common libgcj9-0 libgcj9-jar libifp4 liblua50 liblualib50
  libmodplug0c2 libnjb5 libphonon4 libpq5 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libruby1.8
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x libxvmc1 phonon phonon-backend-gstreamer
  python-qt4 python-qt4-common python-sip4 qt4-qtconfig ruby ruby1.8
  ttf-bengali-fonts ttf-kannada-fonts ttf-liberation ttf-oriya-fonts
  ttf-telugu-fonts ttf-wqy-zenhei tzdata-java
0 upgraded, 0 newly installed, 69 to remove and 0 not upgraded.
After this operation, 289MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128505 files and directories currently installed.)
Removing amarok-common ...
Removing amarok-engine-xine ...
Removing libgcj9-jar ...
Removing libgcj-bc ...
Removing libgcj9-0 ...
rmdir: failed to remove `/var/lib/gcj-4.3': No such file or directory
Removing gcj-4.3-base ...
Removing kde-icons-oxygen ...
Removing kdebase-runtime-data ...
Removing kdebase-runtime-data-common ...
Removing kdelibs4c2a ...
Removing kdelibs-data ...
Removing kdelibs5-data ...
Removing libarts1c2a ...
Removing libartsc0 ...
Removing libavahi-qt3-1 ...
Removing libstreamanalyzer0 ...
Removing libclucene0ldbl ...
Removing libgcj-common ...
Removing libifp4 ...
Removing liblualib50 ...
Removing liblua50 ...
Removing libxine1 ...
Removing libxine1-misc-plugins ...
Removing libmodplug0c2 ...
Removing libnjb5 ...
Removing phonon ...
Removing phonon-backend-gstreamer ...
Removing libphonon4 ...
Removing libpq5 ...
Removing python-qt4 ...
Removing libqt4-assistant ...
Removing qt4-qtconfig ...
Removing libqt4-qt3support ...
Removing libqt4-designer ...
Removing libqt4-script ...
Removing libstrigiqtdbusclient0 ...
Removing libqt4-dbus ...
Removing libqt4-help ...
Removing libqt4-xmlpatterns ...
Removing libqt4-webkit ...
Removing libqt4-network ...
Removing libqt4-opengl ...
Removing libqt4-sql-mysql ...
Removing libqt4-sql ...
Removing libqt4-svg ...
Removing libqt4-test ...
Removing libqt4-xml ...
Removing libqtgui4 ...
Removing libqtcore4 ...
Removing ruby ...
Removing ruby1.8 ...
Removing libruby1.8 ...
Removing libstreams0 ...
Removing libxine1-x ...
Removing libxcb-shape0 ...
Removing libxcb-shm0 ...
Removing libxcb-xv0 ...
Removing libxine1-console ...
Removing libxine1-bin ...
Removing libxvmc1 ...
Removing python-qt4-common ...
Removing python-sip4 ...
Removing ttf-bengali-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-bengali-fonts
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing ttf-kannada-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/ttf-indic-fonts-core
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing ttf-liberation ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing ttf-oriya-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-oriya-fonts
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing ttf-telugu-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-telugu-fonts
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing ttf-wqy-zenhei ...
Updating fontconfig cache for /usr/share/fonts/truetype/wqy
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
Removing tzdata-java ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 



> **taurus said:**
> df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      6.5G  5.9G  262M  96% /
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  108K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.9M  978M   1% /dev
tmpfs                 981M  336K  981M   1% /dev/shm
/dev/sda2              87G  8.3G   79G  10% /host
lrm                   981M  2.0M  979M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M  276K  748K  27% /tmp





Bookmarks are back.
So can I assume it's an issue with space and that I have to change something in the way that space is available?

Also here is what gparted is showing me:

[IMG]http://i34.photobucket.com/albums/d120/iminhell/Screenshot--dev-sda-GParted.png[/IMG]
(I'm more of a visual person)

---

### Post by achase79 on 2009-02-24
your 90gb partition is mounted to the /hosts directory.  So that is where all your free space is located.
Never mind. Your /dev/sda1 partition isn't even mounted.

---

### Post by iminhell on 2009-02-24
sda1 is the Vista partition and IIRC shouldn't be mounted. Sorry I forgot to mention I am dual booting.

---

### Post by achase79 on 2009-02-24
Then your extra space is in the /host directory because that is where the partition is mounted.

---

### Post by iminhell on 2009-02-24
How do I change the free space from /host to be available to all?

---

### Post by iminhell on 2009-03-17
This still is not fixed and I have yet to figure out why. Firefox will not cache anything, I can not download anything to any where on the drive. I'm at a complete loss at what to do and it's very aggravating to run 
```
sudo apt-get clean
sudo apt-get autoremove
```
every 10 minutes of being on the internet, plus having no back option or bookmarks makes things even more difficult.

---

