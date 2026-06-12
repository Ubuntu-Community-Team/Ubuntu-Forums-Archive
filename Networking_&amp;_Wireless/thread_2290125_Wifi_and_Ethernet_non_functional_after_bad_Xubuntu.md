---
title: "Wifi and Ethernet non functional after bad Xubuntu update"
date: 2015-08-09
forum: Networking &amp; Wireless
---

### Post by Amanda_L._Moen on 2015-08-09
[COLOR=#000000]I'm running Xubuntu 14.04, since an update 3 weeks ago I haven't been able to get online. No wifi and no ethernet. (FYI, I'm running dual boot Xubuntu 14.04 / Windows XP Professional SP3 on a Dell Inspiron 1525.)[/COLOR]

[COLOR=#000000]I'm not seeing anyway to even make the text file executable. What the heck am I missing? So, maybe once I figure out how to run the script, I'll be able to figure everything else out.

I ran an update over 3 weeks ago, I'm not sure what happened, but it didn't download properly.  I got a warning letting me know that some files were corrupted in the download.  Since that point in time, my wireless has stopped working.  Earlier this week I finally had the chance to test the ethernet connection, and discovered that wasn't working, either.  To rule out a hardware issue I booted into Windows XP Pro.  Ethernet and wireless both worked just fine while running Windows XP Pro, so not a hardware issue.  I feel that if I could get a clean update of Xubuntu, I'd be just fine.  I think the bad/corrupted files are the cause of my issue.  

When I say ethernet isn't working, I mean that the link light doesn't even come on when plugging the cable into the computer directly from the modem.  When running Windows, the link light does come on.

What can I do to get the ethernet back up and running so I can run updates?
[/COLOR]
Thank you so much for helping me.  (I find screen shots very helpful.)

---

### Post by Hadaka on 2015-08-09
Hi, please open a terminal and do..
```
lspci -n | egrep "0200|0280" | awk '{print$3}'
rfkill list all | grep -i yes
lsmod | grep -i wl
```
post the output
thanks

---

### Post by Amanda_L._Moen on 2015-08-09
Did that, here's the output:
> 11ab:4354
14e4:4328

---

### Post by Hadaka on 2015-08-09
ok,thanks...let's try this first...reboot your computer
as it is booting up..hold down the SHIFT key...this should
put it into the recovery mode...choose Previous Linux Version kernel and boot
to it...see if everything works then, Please do that and then report
back and we will go from there,.
thanks.

---

### Post by Amanda_L._Moen on 2015-08-10
Okay, I did that.  I have wifi functioning again, so thank you very much for that.  With the way I have it set up I had to choose the start Ubuntu with advanced options, and choose one of the previous recovery kernels.  Once I did that my wireless card started functioning again.  Woohoo! :KS

Not sure if this next part should be in its own thread...  

What would be the simplest way to check the space on the partition?  Best way to quickly remove old/outdated files/folders/archives?

Now my problem appears to be one of space.  
```
amandalmoen@Amanda-Inspiron-1525:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdbd-mysql-perl libdbi-perl libmysqlclient18 libterm-readkey-perl
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.13.0-57 linux-headers-3.13.0-57-generic
  linux-image-extra-3.13.0-57-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-57 linux-headers-3.13.0-57-generic
  linux-image-extra-3.13.0-57-generic
0 upgraded, 3 newly installed, 0 to remove and 14 not upgraded.
3 not fully installed or removed.
Need to get 0 B/46.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 586422 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.13.0-57-generic_3.13.0-57.95_i386.deb ...
Unpacking linux-image-extra-3.13.0-57-generic (3.13.0-57.95) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-3.13.0-57-generic_3.13.0-57.95_i386.deb (--unpack):
 unable to create `/lib/modules/3.13.0-57-generic/kernel/drivers/input/touchscreen/bu21013_ts.ko.dpkg-new' (while processing `./lib/modules/3.13.0-57-generic/kernel/drivers/input/touchscreen/bu21013_ts.ko'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-57_3.13.0-57.95_all.deb ...
Unpacking linux-headers-3.13.0-57 (3.13.0-57.95) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-57_3.13.0-57.95_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-57/include/sound/rcar_snd.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-57/include/sound/rcar_snd.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-57-generic_3.13.0-57.95_i386.deb ...
Unpacking linux-headers-3.13.0-57-generic (3.13.0-57.95) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-57-generic_3.13.0-57.95_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-57-generic/include/config/input/yealink.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-57-generic/include/config/input/yealink.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-3.13.0-57-generic_3.13.0-57.95_i386.deb
 /var/cache/apt/archives/linux-headers-3.13.0-57_3.13.0-57.95_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-57-generic_3.13.0-57.95_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Hadaka on 2015-08-10
ok,thats a step forward, please post the output of..
```
df -i
uname -r
sudo dpkg --list 'linux-image*' | awk '{print $2}'
```
thanks.

---

### Post by Amanda_L._Moen on 2015-08-10
Here are the results:

```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda7      610800 610190    610  100% /
none           213723      2 213721    1% /sys/fs/cgroup
udev           208921    510 208411    1% /dev
tmpfs          213723    556 213167    1% /run
none           213723      3 213720    1% /run/lock
none           213723      6 213717    1% /run/shm
none           213723     29 213694    1% /run/user
/dev/sda8      864960  56286 808674    7% /home
```

```
3.13.0-55-generic
```

```
Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
Err?=(none)/Reinst-required
Name

linux-image
linux-image-3.0
linux-image-3.11.0-12-generic
linux-image-3.11.0-20-generic
linux-image-3.13.0-24-generic
linux-image-3.13.0-27-generic
linux-image-3.13.0-32-generic
linux-image-3.13.0-35-generic
linux-image-3.13.0-36-generic
linux-image-3.13.0-37-generic
linux-image-3.13.0-39-generic
linux-image-3.13.0-40-generic
linux-image-3.13.0-43-generic
linux-image-3.13.0-44-generic
linux-image-3.13.0-45-generic
linux-image-3.13.0-49-generic
linux-image-3.13.0-52-generic
linux-image-3.13.0-53-generic
linux-image-3.13.0-55-generic
linux-image-3.13.0-57-generic
linux-image-extra-3.11.0-12-generic
linux-image-extra-3.11.0-20-generic
linux-image-extra-3.13.0-24-generic
linux-image-extra-3.13.0-27-generic
linux-image-extra-3.13.0-32-generic
linux-image-extra-3.13.0-35-generic
linux-image-extra-3.13.0-36-generic
linux-image-extra-3.13.0-37-generic
linux-image-extra-3.13.0-39-generic
linux-image-extra-3.13.0-40-generic
linux-image-extra-3.13.0-43-generic
linux-image-extra-3.13.0-44-generic
linux-image-extra-3.13.0-45-generic
linux-image-extra-3.13.0-49-generic
linux-image-extra-3.13.0-52-generic
linux-image-extra-3.13.0-53-generic
linux-image-extra-3.13.0-55-generic
linux-image-extra-3.13.0-57-generic
linux-image-generic
```

---

### Post by Hadaka on 2015-08-10
thanks, as you can see above you have 100% usage in sda7
so let;s see if we can clear some area to use by deleting some old kernels.
please COPY and paste...one line at a time...and there are about 26 lines
the first set of commands will not output anything.,,and take about 2 to 4 minutes
to complete and will then just return you to your regular terminal prompt. **IF
the command takes more than 5 minutes to complete, press ctrl/c and then enter
the next command in line.
please do..one line at a time
```
sudo rm -rf /usr/src/linux-image-extra-3.11.0-12-generic
sudo rm -rf /usr/src/linux-image-extra-3.11.0-20-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-24-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-27-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-32-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-35-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-36-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-37-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-39-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-40-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-43-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-44-generic
sudo rm -rf /usr/src/linux-image-extra-3.13.0-45-generic
```
and then..these commands will output alot of data..
```
sudo dpkg --purge linux-image-extra-3.11.0-12-generic
sudo dpkg --purge linux-image-extra-3.11.0-20-generic
sudo dpkg --purge linux-image-extra-3.13.0-24-generic
sudo dpkg --purge linux-image-extra-3.13.0-27-generic
sudo dpkg --purge linux-image-extra-3.13.0-32-generic
sudo dpkg --purge linux-image-extra-3.13.0-35-generic
sudo dpkg --purge linux-image-extra-3.13.0-36-generic
sudo dpkg --purge linux-image-extra-3.13.0-37-generic
sudo dpkg --purge linux-image-extra-3.13.0-39-generic
sudo dpkg --purge linux-image-extra-3.13.0-40-generic
sudo dpkg --purge linux-image-extra-3.13.0-43-generic
sudo dpkg --purge linux-image-extra-3.13.0-44-generic
sudo dpkg --purge linux-image-extra-3.13.0-45-generic
```

i do not need any output from this..just let me know it ran ok,
almost there when these are done...let us know how it went
thanks.

---

### Post by Amanda_L._Moen on 2015-08-10
Okay, I completed that.

---

### Post by Hadaka on 2015-08-10
great..that was the linux -image-extra....we may need to do the other
lets take a look at the inode usage in sda7 now...please do and post
```
df -i
sudo dpkg --list 'linux-image*' | awk '{print$1,$2}'
```
thanks
we are getting close

---

### Post by Amanda_L._Moen on 2015-08-10
Okay, here we go:
```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda7      610800 560934  49866   92% /
none           213723      2 213721    1% /sys/fs/cgroup
udev           208921    517 208404    1% /dev
tmpfs          213723    573 213150    1% /run
none           213723      3 213720    1% /run/lock
none           213723      9 213714    1% /run/shm
none           213723     34 213689    1% /run/user
/dev/sda8      864960  56308 808652    7% /home
```

```
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required
||/ Name
+++-=================================================-====================================-============-==================================================================================== 
un linux-image
un linux-image-3.0
rc linux-image-3.11.0-12-generic
ii linux-image-3.11.0-20-generic
ii linux-image-3.13.0-24-generic
ii linux-image-3.13.0-27-generic
ii linux-image-3.13.0-32-generic
ii linux-image-3.13.0-35-generic
ii linux-image-3.13.0-36-generic
ii linux-image-3.13.0-37-generic
ii linux-image-3.13.0-39-generic
ii linux-image-3.13.0-40-generic
ii linux-image-3.13.0-43-generic
ii linux-image-3.13.0-44-generic
ii linux-image-3.13.0-45-generic
ii linux-image-3.13.0-49-generic
ii linux-image-3.13.0-52-generic
ii linux-image-3.13.0-53-generic
ii linux-image-3.13.0-55-generic
ii linux-image-3.13.0-57-generic
ii linux-image-extra-3.13.0-49-generic
ii linux-image-extra-3.13.0-52-generic
ii linux-image-extra-3.13.0-53-generic
ii linux-image-extra-3.13.0-55-generic
in linux-image-extra-3.13.0-57-generic
iU linux-image-generic
```

---

### Post by Hadaka on 2015-08-10
yes we need to do the non extra image also..so do these
you know the routine..
```
sudo rm -rf /usr/src/linux-image-3.11.0-12-generic
sudo rm -rf /usr/src/linux-image-3.11.0-20-generic
sudo rm -rf /usr/src/linux-image-3.13.0-24-generic
sudo rm -rf /usr/src/linux-image-3.13.0-27-generic
sudo rm -rf /usr/src/linux-image-3.13.0-32-generic
sudo rm -rf /usr/src/linux-image-3.13.0-35-generic
sudo rm -rf /usr/src/linux-image-3.13.0-36-generic
sudo rm -rf /usr/src/linux-image-3.13.0-37-generic
sudo rm -rf /usr/src/linux-image-3.13.0-39-generic
sudo rm -rf /usr/src/linux-image-3.13.0-40-generic
sudo rm -rf /usr/src/linux-image-3.13.0-43-generic
sudo rm -rf /usr/src/linux-image-3.13.0-44-generic
sudo rm -rf /usr/src/linux-image-3.13.0-45-generic
```
and then..
```
sudo dpkg --purge linux-image-3.11.0-12-generic
sudo dpkg --purge linux-image-3.11.0-20-generic
sudo dpkg --purge linux-image-3.13.0-24-generic
sudo dpkg --purge linux-image-3.13.0-27-generic
sudo dpkg --purge linux-image-3.13.0-32-generic
sudo dpkg --purge linux-image-3.13.0-35-generic
sudo dpkg --purge linux-image-3.13.0-36-generic
sudo dpkg --purge linux-image-3.13.0-37-generic
sudo dpkg --purge linux-image-3.13.0-39-generic
sudo dpkg --purge linux-image-3.13.0-40-generic
sudo dpkg --purge linux-image-3.13.0-43-generic
sudo dpkg --purge linux-image-3.13.0-44-generic
sudo dpkg --purge linux-image-3.13.0-45-generic
```
then once again post..
```
df -i
sudo dpkg --list 'linux-image*' | awk '{print$1,$2}'
```
thanks

---

### Post by Amanda_L._Moen on 2015-08-10
```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda7      610800 550159  60641   91% /
none           213723      2 213721    1% /sys/fs/cgroup
udev           208921    517 208404    1% /dev
tmpfs          213723    575 213148    1% /run
none           213723      3 213720    1% /run/lock
none           213723     11 213712    1% /run/shm
none           213723     36 213687    1% /run/user
/dev/sda8      864960  56487 808473    7% /home
```

```
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required
||/ Name
+++-=================================================-====================================-============-==================================================================================== 
un linux-image
un linux-image-3.0
ii linux-image-3.13.0-49-generic
ii linux-image-3.13.0-52-generic
ii linux-image-3.13.0-53-generic
ii linux-image-3.13.0-55-generic
ii linux-image-3.13.0-57-generic
ii linux-image-extra-3.13.0-49-generic
ii linux-image-extra-3.13.0-52-generic
ii linux-image-extra-3.13.0-53-generic
ii linux-image-extra-3.13.0-55-generic
in linux-image-extra-3.13.0-57-generic
iU linux-image-generic
```

---

### Post by Hadaka on 2015-08-10
something is still holding that inode count at 91%...please post
```
ls -al
```
I think we have deleted eveery linux-image except the corrupt one..
first ***MAKE SURE you are on Linux -image 3.13.0-55-generic*
check with..
```
uname r
```
*If and only if it is ** Linux -image 3.13.0-55 **
then do..
Ignore any  file not found or minor error messages do all 4 lines
one at a time
```
sudo rm -rf /usr/src/linux-image-extra-3.13.0-57-generic
sudo dpkg --purge linux-image-extra-3.13.0-57-generic
sudo rm -rf /usr/src/linux-image-3.13.0-57-generic
sudo dpkg --purge linux-image-3.13.0-57-generic
```
see if these will run
```
sudo apt-get autoremove
sudo apt-get update
```

---

### Post by Amanda_L._Moen on 2015-08-10
```
total 17720
drwxr-xr-x 65 amandalmoen amandalmoen   20480 Aug 10 17:51 .
drwxr-xr-x  4 root        root           4096 May  5  2014 ..
-rw-rw-r--  1 amandalmoen amandalmoen    5916 May 19  2014 abspath.c
-rw-rw-r--  1 amandalmoen amandalmoen    1473 May 19  2014 aclocal.m4
drwx------  3 amandalmoen amandalmoen    4096 May 12  2014 .adobe
-rw-rw-r--  1 amandalmoen amandalmoen    3302 May 19  2014 advice.c
-rw-rw-r--  1 amandalmoen amandalmoen     927 May 19  2014 advice.h
-rw-rw-r--  1 amandalmoen amandalmoen    1747 May 19  2014 alias.c
-rw-rw-r--  1 amandalmoen amandalmoen    1675 May 19  2014 alloc.c
-rw-rw-r--  1 amandalmoen amandalmoen   12634 May 19  2014 archive.c
-rw-rw-r--  1 amandalmoen amandalmoen    1382 May 19  2014 archive.h
-rw-rw-r--  1 amandalmoen amandalmoen   11289 May 19  2014 archive-tar.c
-rw-rw-r--  1 amandalmoen amandalmoen   12403 May 19  2014 archive-zip.c
-rw-rw-r--  1 amandalmoen amandalmoen    1816 May 19  2014 argv-array.c
-rw-rw-r--  1 amandalmoen amandalmoen     696 May 19  2014 argv-array.h
-rw-rw-r--  1 amandalmoen amandalmoen   19495 May 19  2014 attr.c
-rw-rw-r--  1 amandalmoen amandalmoen    1616 May 19  2014 attr.h
-rw-rw-r--  1 amandalmoen amandalmoen    2825 May 19  2014 base85.c
-rw-------  1 amandalmoen amandalmoen   14290 Aug  9 22:33 .bash_history
-rw-r--r--  1 amandalmoen amandalmoen     220 May  5  2014 .bash_logout
-rw-rw-r--  1 amandalmoen amandalmoen       1 May 23  2014 .bash_profile
-rw-r--r--  1 amandalmoen amandalmoen    3746 May 23  2014 .bashrc
-rw-rw-r--  1 amandalmoen amandalmoen   24139 May 19  2014 bisect.c
-rw-rw-r--  1 amandalmoen amandalmoen     644 May 19  2014 bisect.h
-rw-rw-r--  1 amandalmoen amandalmoen     565 May 19  2014 blob.c
-rw-rw-r--  1 amandalmoen amandalmoen     664 May 19  2014 blob.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 block-sha1
-rw-rw-r--  1 amandalmoen amandalmoen    8317 May 19  2014 branch.c
-rw-rw-r--  1 amandalmoen amandalmoen    1994 May 19  2014 branch.h
-rwxrwxr-x  1 amandalmoen amandalmoen     283 May 23  2014 build_gh_pages.sh
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 builtin
-rw-rw-r--  1 amandalmoen amandalmoen    8713 May 19  2014 builtin.h
-rw-rw-r--  1 amandalmoen amandalmoen    7210 May 19  2014 bulk-checkin.c
-rw-rw-r--  1 amandalmoen amandalmoen     343 May 19  2014 bulk-checkin.h
-rw-rw-r--  1 amandalmoen amandalmoen   11249 May 19  2014 bundle.c
-rw-rw-r--  1 amandalmoen amandalmoen     707 May 19  2014 bundle.h
-rw-rw-r--  1 amandalmoen amandalmoen       0 Jul 16 14:40 ???@@?C@8?@
drwx------ 19 amandalmoen amandalmoen    4096 Aug 10 19:30 .cache
-rw-rw-r--  1 amandalmoen amandalmoen   52560 May 19  2014 cache.h
-rw-rw-r--  1 amandalmoen amandalmoen   16736 May 19  2014 cache-tree.c
-rw-rw-r--  1 amandalmoen amandalmoen    1546 May 19  2014 cache-tree.h
drwxrwxr-x  5 amandalmoen amandalmoen    4096 Jul  8 19:25 Canopy
-rwxrwxr-x  1 amandalmoen amandalmoen     369 May 19  2014 check_bindir
-rwxrwxr-x  1 amandalmoen amandalmoen     590 May 19  2014 check-builtins.sh
-rw-rw-r--  1 amandalmoen amandalmoen     538 May 19  2014 check-racy.c
drwxrwxr-x 15 amandalmoen amandalmoen    4096 Apr 23 19:17 code
-rw-rw-r--  1 amandalmoen amandalmoen    5366 May 19  2014 color.c
-rw-rw-r--  1 amandalmoen amandalmoen    3190 May 19  2014 color.h
-rw-rw-r--  1 amandalmoen amandalmoen   10407 May 19  2014 column.c
-rw-rw-r--  1 amandalmoen amandalmoen    1477 May 19  2014 column.h
-rw-rw-r--  1 amandalmoen amandalmoen   37833 May 19  2014 combine-diff.c
-rw-rw-r--  1 amandalmoen amandalmoen    8091 May 19  2014 command-list.txt
-rw-rw-r--  1 amandalmoen amandalmoen   38741 May 19  2014 commit.c
-rw-rw-r--  1 amandalmoen amandalmoen   10540 May 19  2014 commit.h
-rw-rw-r--  1 amandalmoen amandalmoen    3824 May 19  2014 commit-slab.h
drwxrwxr-x  7 amandalmoen amandalmoen    4096 May 19  2014 compat
drwx------ 27 amandalmoen amandalmoen    4096 Jul 28 15:37 .config
-rw-rw-r--  1 amandalmoen amandalmoen   44500 May 19  2014 config.c
-rw-rw-r--  1 amandalmoen amandalmoen     540 May 19  2014 config.mak.in
-rw-rw-r--  1 amandalmoen amandalmoen   15482 May 19  2014 config.mak.uname
-rw-rw-r--  1 amandalmoen amandalmoen   32144 May 19  2014 configure.ac
-rw-rw-r--  1 amandalmoen amandalmoen   17963 May 19  2014 connect.c
-rw-rw-r--  1 amandalmoen amandalmoen    3338 May 19  2014 connected.c
-rw-rw-r--  1 amandalmoen amandalmoen     930 May 19  2014 connected.h
-rw-rw-r--  1 amandalmoen amandalmoen     596 May 19  2014 connect.h
drwxrwxr-x 26 amandalmoen amandalmoen    4096 May 19  2014 contrib
-rw-rw-r--  1 amandalmoen amandalmoen   29898 May 19  2014 convert.c
-rw-rw-r--  1 amandalmoen amandalmoen    2216 May 19  2014 convert.h
-rw-rw-r--  1 amandalmoen amandalmoen    1590 May 19  2014 copy.c
-rw-rw-r--  1 amandalmoen amandalmoen   18765 May 19  2014 COPYING
-rw-rw-r--  1 amandalmoen amandalmoen    7756 May 19  2014 credential.c
-rw-rw-r--  1 amandalmoen amandalmoen    2985 May 19  2014 credential-cache.c
-rw-rw-r--  1 amandalmoen amandalmoen    6009 May 19  2014 credential-cache--daemon.c
-rw-rw-r--  1 amandalmoen amandalmoen     822 May 19  2014 credential.h
-rw-rw-r--  1 amandalmoen amandalmoen    4052 May 19  2014 credential-store.c
-rw-rw-r--  1 amandalmoen amandalmoen    4151 May 19  2014 csum-file.c
-rw-rw-r--  1 amandalmoen amandalmoen    1084 May 19  2014 csum-file.h
-rw-rw-r--  1 amandalmoen amandalmoen    2659 May 19  2014 ctype.c
-rw-rw-r--  1 amandalmoen amandalmoen   30974 May 19  2014 daemon.c
-rw-rw-r--  1 amandalmoen amandalmoen   25993 May 19  2014 date.c
drwx------  3 amandalmoen amandalmoen    4096 May  5  2014 .dbus
-rw-rw-r--  1 amandalmoen amandalmoen    1890 May 19  2014 decorate.c
-rw-rw-r--  1 amandalmoen amandalmoen     400 May 19  2014 decorate.h
-rw-rw-r--  1 amandalmoen amandalmoen    3464 May 19  2014 delta.h
drwxr-xr-x  3 amandalmoen amandalmoen    4096 Aug  9 15:31 Desktop
-rw-rw-r--  1 amandalmoen amandalmoen  137996 May 19  2014 diff.c
-rw-rw-r--  1 amandalmoen amandalmoen    8979 May 19  2014 diffcore-break.c
-rw-rw-r--  1 amandalmoen amandalmoen    5488 May 19  2014 diffcore-delta.c
-rw-rw-r--  1 amandalmoen amandalmoen    4836 May 19  2014 diffcore.h
-rw-rw-r--  1 amandalmoen amandalmoen    2492 May 19  2014 diffcore-order.c
-rw-rw-r--  1 amandalmoen amandalmoen    5865 May 19  2014 diffcore-pickaxe.c
-rw-rw-r--  1 amandalmoen amandalmoen   17722 May 19  2014 diffcore-rename.c
-rw-rw-r--  1 amandalmoen amandalmoen   15811 May 19  2014 diff-delta.c
-rw-rw-r--  1 amandalmoen amandalmoen   11558 May 19  2014 diff.h
-rw-rw-r--  1 amandalmoen amandalmoen   14206 May 19  2014 diff-lib.c
-rw-rw-r--  1 amandalmoen amandalmoen    5589 May 19  2014 diff-no-index.c
-rw-rw-r--  1 amandalmoen amandalmoen   42370 May 19  2014 dir.c
-rw-rw-r--  1 amandalmoen amandalmoen    7089 May 19  2014 dir.h
-rw-r--r--  1 amandalmoen amandalmoen      41 May  5  2014 .dmrc
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 23  2014 docs
drwxrwxr-x  5 amandalmoen amandalmoen   12288 May 19  2014 Documentation
drwxr-xr-x  2 amandalmoen amandalmoen    4096 Jun 10 09:08 Documents
drwxr-xr-x  2 amandalmoen amandalmoen    4096 Aug  9 22:17 Downloads
-rw-rw-r--  1 amandalmoen amandalmoen    1556 May 19  2014 editor.c
-rw-rw-r--  1 amandalmoen amandalmoen    7437 May 19  2014 entry.c
-rw-rw-r--  1 amandalmoen amandalmoen    7726 May 19  2014 environment.c
drwxrwxr-x  4 amandalmoen amandalmoen    4096 May 10  2014 etc
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 ewah
-rw-rw-r--  1 amandalmoen amandalmoen    3307 May 19  2014 exec_cmd.c
-rw-rw-r--  1 amandalmoen amandalmoen     509 May 19  2014 exec_cmd.h
-rw-rw-r--  1 amandalmoen amandalmoen   89687 May 19  2014 fast-import.c
-rw-rw-r--  1 amandalmoen amandalmoen   26529 May 19  2014 fetch-pack.c
-rw-rw-r--  1 amandalmoen amandalmoen    1049 May 19  2014 fetch-pack.h
-rw-rw-r--  1 amandalmoen amandalmoen     187 May 19  2014 fmt-merge-msg.h
-rw-rw-r--  1 amandalmoen amandalmoen   10385 May 19  2014 fsck.c
-rw-rw-r--  1 amandalmoen amandalmoen    1062 May 19  2014 fsck.h
drwx------  5 amandalmoen amandalmoen    4096 Aug 10 16:04 .gconf
-rwxrwxr-x  1 amandalmoen amandalmoen     433 May 19  2014 generate-cmdlist.sh
-rw-rw-r--  1 amandalmoen amandalmoen    4359 May 19  2014 gettext.c
-rw-rw-r--  1 amandalmoen amandalmoen    1455 May 19  2014 gettext.h
drwxrwxr-x 20 amandalmoen amandalmoen   16384 May 16 16:52 git
drwxrwxr-x  8 amandalmoen amandalmoen    4096 May 28  2014 .git
-rwxrwxr-x  1 amandalmoen amandalmoen   36871 May 19  2014 git-add--interactive.perl
-rwxrwxr-x  1 amandalmoen amandalmoen   23271 May 19  2014 git-am.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   36893 May 19  2014 git-archimport.perl
-rw-rw-r--  1 amandalmoen amandalmoen     105 May 19  2014 .gitattributes
-rwxrwxr-x  1 amandalmoen amandalmoen   11993 May 19  2014 git-bisect.sh
-rw-rw-r--  1 amandalmoen amandalmoen   18232 May 19  2014 git.c
-rw-rw-r--  1 amandalmoen amandalmoen   18437 May 19  2014 git-compat-util.h
-rw-rw-r--  1 amandalmoen amandalmoen      90 May 16 16:50 .gitconfig
-rwxrwxr-x  1 amandalmoen amandalmoen   12862 May 19  2014 git-cvsexportcommit.perl
-rwxrwxr-x  1 amandalmoen amandalmoen   32019 May 19  2014 git-cvsimport.perl
-rwxrwxr-x  1 amandalmoen amandalmoen  162359 May 19  2014 git-cvsserver.perl
-rwxrwxr-x  1 amandalmoen amandalmoen    1968 May 19  2014 git-difftool--helper.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   13250 May 19  2014 git-difftool.perl
-rwxrwxr-x  1 amandalmoen amandalmoen   11663 May 19  2014 git-filter-branch.sh
drwxrwxr-x  6 amandalmoen amandalmoen    4096 May 19  2014 git-gui
-rw-rw-r--  1 amandalmoen amandalmoen    4926 May 28  2014 .gitignore
-rwxrwxr-x  1 amandalmoen amandalmoen   18260 May 19  2014 git-instaweb.sh
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 19  2014 gitk-git
-rwxrwxr-x  1 amandalmoen amandalmoen    2207 May 19  2014 git-merge-octopus.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    3482 May 19  2014 git-merge-one-file.sh
-rwxrwxr-x  1 amandalmoen amandalmoen     944 May 19  2014 git-merge-resolve.sh
-rw-rw-r--  1 amandalmoen amandalmoen    7562 May 19  2014 git-mergetool--lib.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    8377 May 19  2014 git-mergetool.sh
-rwxrwxr-x  1 amandalmoen amandalmoen  122142 May 19  2014 git-p4.py
-rw-rw-r--  1 amandalmoen amandalmoen    2313 May 19  2014 git-parse-remote.sh
-rw-rw-r--  1 amandalmoen amandalmoen   15375 May 23  2014 .git-prompt.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    8926 May 19  2014 git-pull.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    3368 May 19  2014 git-quiltimport.sh
-rw-rw-r--  1 amandalmoen amandalmoen     566 May 19  2014 git.rc
-rw-rw-r--  1 amandalmoen amandalmoen    2242 May 19  2014 git-rebase--am.sh
-rw-rw-r--  1 amandalmoen amandalmoen   28505 May 19  2014 git-rebase--interactive.sh
-rw-rw-r--  1 amandalmoen amandalmoen    3787 May 19  2014 git-rebase--merge.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   15769 May 19  2014 git-rebase.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    4130 May 19  2014 git-relink.perl
-rwxrwxr-x  1 amandalmoen amandalmoen    2755 May 19  2014 git-remote-testgit.sh
-rwxrwxr-x  1 amandalmoen amandalmoen    3856 May 19  2014 git-request-pull.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   44082 May 19  2014 git-send-email.perl
-rw-rw-r--  1 amandalmoen amandalmoen    2012 May 19  2014 git-sh-i18n.sh
-rw-rw-r--  1 amandalmoen amandalmoen    8276 May 19  2014 git-sh-setup.sh
-rw-rw-r--  1 amandalmoen amandalmoen   11338 May 19  2014 git.spec.in
-rwxrwxr-x  1 amandalmoen amandalmoen   13560 May 19  2014 git-stash.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   32201 May 19  2014 git-submodule.sh
-rwxrwxr-x  1 amandalmoen amandalmoen   61041 May 19  2014 git-svn.perl
-rwxrwxr-x  1 amandalmoen amandalmoen     768 May 19  2014 GIT-VERSION-GEN
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 19  2014 gitweb
-rwxrwxr-x  1 amandalmoen amandalmoen    4398 May 19  2014 git-web--browse.sh
-rw-r-----  1 amandalmoen amandalmoen       0 Aug  9 22:15 .gksu.lock
drwx------  5 amandalmoen amandalmoen    4096 Jul  8 18:40 .gnome2
drwx------  2 amandalmoen amandalmoen    4096 Oct  1  2014 .gnome2_private
drwxr-xr-x 11 amandalmoen amandalmoen    4096 Jul 17  2013 gnotime-2.4.0
-rw-rw-r--  1 amandalmoen amandalmoen    3812 May 19  2014 gpg-interface.c
-rw-rw-r--  1 amandalmoen amandalmoen     721 May 19  2014 gpg-interface.h
-rw-rw-r--  1 amandalmoen amandalmoen   35668 May 19  2014 graph.c
-rw-rw-r--  1 amandalmoen amandalmoen    4010 May 19  2014 graph.h
-rw-rw-r--  1 amandalmoen amandalmoen   41617 May 19  2014 grep.c
-rw-rw-r--  1 amandalmoen amandalmoen    4843 May 19  2014 grep.h
drwxr-xr-x  2 amandalmoen amandalmoen    4096 Jul 16 14:28 .gstreamer-0.10
drwxrwxr-x  9 amandalmoen amandalmoen    4096 Jul 16 14:29 hamster-master
-rw-rw-r--  1 amandalmoen amandalmoen    5535 May 19  2014 hashmap.c
-rw-rw-r--  1 amandalmoen amandalmoen    1892 May 19  2014 hashmap.h
-rw-rw-r--  1 amandalmoen amandalmoen   11324 May 19  2014 help.c
-rw-rw-r--  1 amandalmoen amandalmoen    1115 May 19  2014 help.h
-rw-rw-r--  1 amandalmoen amandalmoen    2342 May 19  2014 hex.c
drwxr-----  2 amandalmoen amandalmoen    4096 Aug  8  2014 .hplip
-rw-rw-r--  1 amandalmoen amandalmoen   14241 May 19  2014 http-backend.c
-rw-rw-r--  1 amandalmoen amandalmoen   39486 May 19  2014 http.c
-rw-rw-r--  1 amandalmoen amandalmoen    2321 May 19  2014 http-fetch.c
-rw-rw-r--  1 amandalmoen amandalmoen    6264 May 19  2014 http.h
-rw-rw-r--  1 amandalmoen amandalmoen   51687 May 19  2014 http-push.c
-rw-rw-r--  1 amandalmoen amandalmoen   14285 May 19  2014 http-walker.c
-rw-------  1 amandalmoen amandalmoen   13090 Aug 10 16:04 .ICEauthority
-rw-rw-r--  1 amandalmoen amandalmoen   10671 May 19  2014 ident.c
-rw-rw-r--  1 amandalmoen amandalmoen   33679 May 19  2014 imap-send.c
-rw-rw-r--  1 amandalmoen amandalmoen    8714 May 19  2014 INSTALL
-rw-rw-r--  1 amandalmoen amandalmoen   13418 May 19  2014 khash.h
-rw-rw-r--  1 amandalmoen amandalmoen   20994 May 19  2014 kwset.c
-rw-rw-r--  1 amandalmoen amandalmoen    2613 May 19  2014 kwset.h
-rw-rw-r--  1 amandalmoen amandalmoen    2597 May 19  2014 levenshtein.c
-rw-rw-r--  1 amandalmoen amandalmoen     203 May 19  2014 levenshtein.h
-rw-rw-r--  1 amandalmoen amandalmoen   26859 May 19  2014 LGPL-2.1
-rw-rw-r--  1 amandalmoen amandalmoen   31467 May 19  2014 line-log.c
-rw-rw-r--  1 amandalmoen amandalmoen    1850 May 19  2014 line-log.h
-rw-rw-r--  1 amandalmoen amandalmoen    6639 May 19  2014 line-range.c
-rw-rw-r--  1 amandalmoen amandalmoen    1336 May 19  2014 line-range.h
-rw-rw-r--  1 amandalmoen amandalmoen    6200 May 19  2014 list-objects.c
-rw-rw-r--  1 amandalmoen amandalmoen     407 May 19  2014 list-objects.h
-rw-rw-r--  1 amandalmoen amandalmoen   10404 May 19  2014 ll-merge.c
-rw-rw-r--  1 amandalmoen amandalmoen     567 May 19  2014 ll-merge.h
drwxr-xr-x  3 amandalmoen amandalmoen    4096 May  5  2014 .local
-rw-rw-r--  1 amandalmoen amandalmoen    6434 May 19  2014 lockfile.c
-rw-rw-r--  1 amandalmoen amandalmoen   22861 May 19  2014 log-tree.c
-rw-rw-r--  1 amandalmoen amandalmoen    1015 May 19  2014 log-tree.h
drwx------  3 amandalmoen amandalmoen    4096 May 12  2014 .macromedia
-rw-rw-r--  1 amandalmoen amandalmoen   13844 May 19  2014 .mailmap
-rw-rw-r--  1 amandalmoen amandalmoen    9337 May 19  2014 mailmap.c
-rw-rw-r--  1 amandalmoen amandalmoen     271 May 19  2014 mailmap.h
-rw-rw-r--  1 amandalmoen amandalmoen   91310 May 28  2014 Makefile
-rw-rw-r--  1 amandalmoen amandalmoen    8380 May 19  2014 match-trees.c
-rw-rw-r--  1 amandalmoen amandalmoen    2676 May 19  2014 merge-blobs.c
-rw-rw-r--  1 amandalmoen amandalmoen     194 May 19  2014 merge-blobs.h
-rw-rw-r--  1 amandalmoen amandalmoen    2886 May 19  2014 merge.c
-rw-rw-r--  1 amandalmoen amandalmoen   59578 May 19  2014 merge-recursive.c
-rw-rw-r--  1 amandalmoen amandalmoen    1602 May 19  2014 merge-recursive.h
-rw-rw-r--  1 amandalmoen amandalmoen    1514 May 19  2014 mergesort.c
-rw-rw-r--  1 amandalmoen amandalmoen     574 May 19  2014 mergesort.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 mergetools
drwx------  4 amandalmoen amandalmoen    4096 May  5  2014 .mozilla
drwxr-xr-x  2 amandalmoen amandalmoen    4096 May  5  2014 Music
-rw-------  1 amandalmoen amandalmoen     399 May 11 18:24 .mysql_history
-rw-rw-r--  1 amandalmoen amandalmoen    6462 May 19  2014 name-hash.c
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 23  2014 notes
-rw-rw-r--  1 amandalmoen amandalmoen   36948 May 19  2014 notes.c
-rw-rw-r--  1 amandalmoen amandalmoen    2282 May 19  2014 notes-cache.c
-rw-rw-r--  1 amandalmoen amandalmoen     500 May 19  2014 notes-cache.h
-rw-rw-r--  1 amandalmoen amandalmoen   11519 May 19  2014 notes.h
-rw-rw-r--  1 amandalmoen amandalmoen   23154 May 19  2014 notes-merge.c
-rw-rw-r--  1 amandalmoen amandalmoen    2998 May 19  2014 notes-merge.h
-rw-rw-r--  1 amandalmoen amandalmoen    4508 May 19  2014 notes-utils.c
-rw-rw-r--  1 amandalmoen amandalmoen    1133 May 19  2014 notes-utils.h
-rw-rw-r--  1 amandalmoen amandalmoen    9749 May 19  2014 object.c
-rw-rw-r--  1 amandalmoen amandalmoen    4402 May 19  2014 object.h
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 12 11:24 opt
-rw-rw-r--  1 amandalmoen amandalmoen   25744 May 19  2014 pack-bitmap.c
-rw-rw-r--  1 amandalmoen amandalmoen    1886 May 19  2014 pack-bitmap.h
-rw-rw-r--  1 amandalmoen amandalmoen   12768 May 19  2014 pack-bitmap-write.c
-rw-rw-r--  1 amandalmoen amandalmoen    5084 May 19  2014 pack-check.c
-rw-rw-r--  1 amandalmoen amandalmoen    3242 May 19  2014 pack.h
-rw-rw-r--  1 amandalmoen amandalmoen    2294 May 19  2014 pack-objects.c
-rw-rw-r--  1 amandalmoen amandalmoen    1918 May 19  2014 pack-objects.h
-rw-rw-r--  1 amandalmoen amandalmoen    7138 May 19  2014 pack-revindex.c
-rw-rw-r--  1 amandalmoen amandalmoen     410 May 19  2014 pack-revindex.h
-rw-rw-r--  1 amandalmoen amandalmoen   10538 May 19  2014 pack-write.c
-rw-rw-r--  1 amandalmoen amandalmoen    3662 May 19  2014 pager.c
-rw-rw-r--  1 amandalmoen amandalmoen   17266 May 19  2014 parse-options.c
-rw-rw-r--  1 amandalmoen amandalmoen    2749 May 19  2014 parse-options-cb.c
-rw-rw-r--  1 amandalmoen amandalmoen    9094 May 19  2014 parse-options.h
-rw-rw-r--  1 amandalmoen amandalmoen    2209 May 19  2014 patch-delta.c
-rw-rw-r--  1 amandalmoen amandalmoen    2480 May 19  2014 patch-ids.c
-rw-rw-r--  1 amandalmoen amandalmoen     490 May 19  2014 patch-ids.h
-rw-rw-r--  1 amandalmoen amandalmoen   18498 May 19  2014 path.c
-rw-rw-r--  1 amandalmoen amandalmoen   14461 May 19  2014 pathspec.c
-rw-rw-r--  1 amandalmoen amandalmoen    3306 May 19  2014 pathspec.h
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 19  2014 perl
drwxr-xr-x  2 amandalmoen amandalmoen    4096 Oct 26  2014 Pictures
drwxr-xr-x  2 root        root           4096 May  5  2014 .pip
-rw-rw-r--  1 amandalmoen amandalmoen    4630 May 19  2014 pkt-line.c
-rw-rw-r--  1 amandalmoen amandalmoen    3102 May 19  2014 pkt-line.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 po
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 ppc
-rw-rw-r--  1 amandalmoen amandalmoen    2517 May 19  2014 preload-index.c
-rw-rw-r--  1 amandalmoen amandalmoen   44089 May 19  2014 pretty.c
-rw-rw-r--  1 amandalmoen amandalmoen  445766 Feb 22 13:06 printertroubleshoot.txt
-rw-rw-r--  1 amandalmoen amandalmoen    1924 May 19  2014 prio-queue.c
-rw-rw-r--  1 amandalmoen amandalmoen    1427 May 19  2014 prio-queue.h
-rw-r--r--  1 amandalmoen amandalmoen     675 May  5  2014 .profile
-rw-rw-r--  1 amandalmoen amandalmoen    6237 May 19  2014 progress.c
-rw-rw-r--  1 amandalmoen amandalmoen     504 May 19  2014 progress.h
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May  5  2014 projects
drwxr-xr-x  5 amandalmoen amandalmoen    4096 May  5  2014 Projects
-rw-rw-r--  1 amandalmoen amandalmoen    1391 May 19  2014 prompt.c
-rw-rw-r--  1 amandalmoen amandalmoen     207 May 19  2014 prompt.h
drwxr-xr-x  2 amandalmoen amandalmoen    4096 May  5  2014 Public
-rw-rw-r--  1 amandalmoen amandalmoen   10398 May 19  2014 quote.c
-rw-rw-r--  1 amandalmoen amandalmoen    2849 May 19  2014 quote.h
-rw-rw-r--  1 amandalmoen amandalmoen    6281 May 19  2014 reachable.c
-rw-rw-r--  1 amandalmoen amandalmoen     163 May 19  2014 reachable.h
-rw-rw-r--  1 amandalmoen amandalmoen   54768 May 19  2014 read-cache.c
-rw-rw-r--  1 amandalmoen amandalmoen    2625 May 19  2014 README
-rw-rw-r--  1 amandalmoen amandalmoen    1841 May 14  2014 README.md
-rw-rw-r--  1 amandalmoen amandalmoen    2848 May 23  2014 README.rst
-rw-rw-r--  1 amandalmoen amandalmoen    8269 May 19  2014 reflog-walk.c
-rw-rw-r--  1 amandalmoen amandalmoen     773 May 19  2014 reflog-walk.h
-rw-rw-r--  1 amandalmoen amandalmoen   95273 May 19  2014 refs.c
-rw-rw-r--  1 amandalmoen amandalmoen    8785 May 19  2014 refs.h
lrwxrwxrwx  1 amandalmoen amandalmoen      32 May 19  2014 RelNotes -> Documentation/RelNotes/2.0.0.txt
-rw-rw-r--  1 amandalmoen amandalmoen   56464 May 19  2014 remote.c
-rw-rw-r--  1 amandalmoen amandalmoen   24744 May 19  2014 remote-curl.c
-rw-rw-r--  1 amandalmoen amandalmoen    7208 May 19  2014 remote.h
-rw-rw-r--  1 amandalmoen amandalmoen    8694 May 19  2014 remote-testsvn.c
-rw-rw-r--  1 amandalmoen amandalmoen    3020 May 19  2014 replace_object.c
-rw-rw-r--  1 amandalmoen amandalmoen     222 May 23  2014 requirements.txt
-rw-rw-r--  1 amandalmoen amandalmoen   18492 May 19  2014 rerere.c
-rw-rw-r--  1 amandalmoen amandalmoen     800 May 19  2014 rerere.h
-rw-rw-r--  1 amandalmoen amandalmoen    4396 May 19  2014 resolve-undo.c
-rw-rw-r--  1 amandalmoen amandalmoen     612 May 19  2014 resolve-undo.h
-rw-rw-r--  1 amandalmoen amandalmoen   90274 May 19  2014 revision.c
-rw-rw-r--  1 amandalmoen amandalmoen    8153 May 19  2014 revision.h
drwxr-xr-x  2 root        root           4096 Aug 10 17:51 .rpmdb
-rw-rw-r--  1 amandalmoen amandalmoen   17437 May 19  2014 run-command.c
-rw-rw-r--  1 amandalmoen amandalmoen    3187 May 19  2014 run-command.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 23  2014 scss_sources
-rw-rw-r--  1 amandalmoen amandalmoen    8537 May 19  2014 send-pack.c
-rw-rw-r--  1 amandalmoen amandalmoen     395 May 19  2014 send-pack.h
-rw-rw-r--  1 amandalmoen amandalmoen   33342 May 19  2014 sequencer.c
-rw-rw-r--  1 amandalmoen amandalmoen    1044 May 19  2014 sequencer.h
-rw-rw-r--  1 amandalmoen amandalmoen    5263 May 19  2014 server-info.c
-rw-rw-r--  1 amandalmoen amandalmoen   23001 May 19  2014 setup.c
-rw-rw-r--  1 amandalmoen amandalmoen    1262 May 19  2014 sha1-array.c
-rw-rw-r--  1 amandalmoen amandalmoen     583 May 19  2014 sha1-array.h
-rw-rw-r--  1 amandalmoen amandalmoen   82647 May 19  2014 sha1_file.c
-rw-rw-r--  1 amandalmoen amandalmoen    9486 May 19  2014 sha1-lookup.c
-rw-rw-r--  1 amandalmoen amandalmoen     403 May 19  2014 sha1-lookup.h
-rw-rw-r--  1 amandalmoen amandalmoen   36747 May 19  2014 sha1_name.c
-rw-rw-r--  1 amandalmoen amandalmoen   18104 May 19  2014 shallow.c
-rw-rw-r--  1 amandalmoen amandalmoen    5299 May 19  2014 shell.c
-rw-rw-r--  1 amandalmoen amandalmoen   10698 May 19  2014 sh-i18n--envsubst.c
-rw-rw-r--  1 amandalmoen amandalmoen     463 May 19  2014 shortlog.h
-rw-rw-r--  1 amandalmoen amandalmoen    2283 May 19  2014 show-index.c
-rw-rw-r--  1 amandalmoen amandalmoen    3477 May 19  2014 sideband.c
-rw-rw-r--  1 amandalmoen amandalmoen     262 May 19  2014 sideband.h
-rw-rw-r--  1 amandalmoen amandalmoen     969 May 19  2014 sigchain.c
-rw-rw-r--  1 amandalmoen amandalmoen     215 May 19  2014 sigchain.h
-rw-rw-r--  1 amandalmoen amandalmoen     272 May 23  2014 slides_requirements.txt
drwxrwxr-x  6 amandalmoen amandalmoen    4096 May 28  2014 source
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 11 12:22 sql
-rw-rw-r--  1 amandalmoen amandalmoen   11828 May 19  2014 strbuf.c
-rw-rw-r--  1 amandalmoen amandalmoen    6278 May 19  2014 strbuf.h
-rw-rw-r--  1 amandalmoen amandalmoen   11992 May 19  2014 streaming.c
-rw-rw-r--  1 amandalmoen amandalmoen     504 May 19  2014 streaming.h
-rw-rw-r--  1 amandalmoen amandalmoen    7592 May 19  2014 string-list.c
-rw-rw-r--  1 amandalmoen amandalmoen    4984 May 19  2014 string-list.h
drwxrwxr-x 20 amandalmoen amandalmoen    4096 May 28  2014 students
drwxrwxr-x  6 amandalmoen amandalmoen    4096 May 24  2014 sublenv
drwxrwxr-x  8 amandalmoen amandalmoen    4096 May 19  2014 SublimeLinter3
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 15  2014 Sublime Text 3
-rw-rw-r--  1 amandalmoen amandalmoen 6150862 Jun 27  2013 sublime-text_build-3047_i386.deb
-rw-rw-r--  1 amandalmoen amandalmoen 6281150 Dec 16  2013 sublime-text_build-3059_i386.deb
-rw-rw-r--  1 amandalmoen amandalmoen   32697 May 19  2014 submodule.c
-rw-rw-r--  1 amandalmoen amandalmoen    1950 May 19  2014 submodule.h
-rw-rw-r--  1 amandalmoen amandalmoen    9613 May 19  2014 symlinks.c
drwxrwxr-x 47 amandalmoen amandalmoen   36864 May 19  2014 t
-rw-rw-r--  1 amandalmoen amandalmoen    4023 May 19  2014 tag.c
-rw-rw-r--  1 amandalmoen amandalmoen     576 May 19  2014 tag.h
-rw-rw-r--  1 amandalmoen amandalmoen     644 May 19  2014 tar.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 templates
drwxr-xr-x  2 amandalmoen amandalmoen    4096 May  5  2014 Templates
-rw-rw-r--  1 amandalmoen amandalmoen    2634 May 19  2014 test-chmtime.c
-rw-rw-r--  1 amandalmoen amandalmoen     918 May 19  2014 test-ctype.c
-rw-rw-r--  1 amandalmoen amandalmoen    1459 May 19  2014 test-date.c
-rw-rw-r--  1 amandalmoen amandalmoen    1801 May 19  2014 test-delta.c
-rw-rw-r--  1 amandalmoen amandalmoen    1586 May 19  2014 test-dump-cache-tree.c
-rw-rw-r--  1 amandalmoen amandalmoen     722 May 19  2014 test-genrandom.c
-rw-rw-r--  1 amandalmoen amandalmoen    5998 May 19  2014 test-hashmap.c
-rw-rw-r--  1 amandalmoen amandalmoen     258 May 19  2014 test-index-version.c
-rw-rw-r--  1 amandalmoen amandalmoen    2148 May 19  2014 test-line-buffer.c
-rw-rw-r--  1 amandalmoen amandalmoen     590 May 19  2014 test-match-trees.c
-rw-rw-r--  1 amandalmoen amandalmoen     924 May 19  2014 test-mergesort.c
-rw-rw-r--  1 amandalmoen amandalmoen     269 May 19  2014 test-mktemp.c
-rw-rw-r--  1 amandalmoen amandalmoen    3435 May 19  2014 test-parse-options.c
-rw-rw-r--  1 amandalmoen amandalmoen    3620 May 19  2014 test-path-utils.c
-rw-rw-r--  1 amandalmoen amandalmoen     621 May 19  2014 test-prio-queue.c
-rw-rw-r--  1 amandalmoen amandalmoen     202 May 19  2014 test-read-cache.c
-rw-rw-r--  1 amandalmoen amandalmoen     534 May 19  2014 test-regex.c
-rw-rw-r--  1 amandalmoen amandalmoen    1393 May 19  2014 test-revision-walking.c
-rw-rw-r--  1 amandalmoen amandalmoen     840 May 19  2014 test-run-command.c
-rw-rw-r--  1 amandalmoen amandalmoen     395 May 19  2014 test-scrap-cache-tree.c
-rw-rw-r--  1 amandalmoen amandalmoen     941 May 19  2014 test-sha1.c
-rwxrwxr-x  1 amandalmoen amandalmoen    1905 May 19  2014 test-sha1.sh
-rw-rw-r--  1 amandalmoen amandalmoen     344 May 19  2014 test-sigchain.c
-rw-rw-r--  1 amandalmoen amandalmoen    2554 May 19  2014 test-string-list.c
-rw-rw-r--  1 amandalmoen amandalmoen     401 May 19  2014 test-subprocess.c
-rw-rw-r--  1 amandalmoen amandalmoen    1332 May 19  2014 test-svn-fe.c
-rw-rw-r--  1 amandalmoen amandalmoen    1240 May 19  2014 test-urlmatch-normalization.c
-rw-rw-r--  1 amandalmoen amandalmoen     635 May 19  2014 test-wildmatch.c
-rw-rw-r--  1 amandalmoen amandalmoen    1297 May 19  2014 thread-utils.c
-rw-rw-r--  1 amandalmoen amandalmoen     209 May 19  2014 thread-utils.h
drwx------  3 amandalmoen amandalmoen    4096 May  5  2014 .thumbnails
drwx------  4 amandalmoen amandalmoen    4096 Sep 14  2014 .thunderbird
-rw-rw-r--  1 amandalmoen amandalmoen    4801 May 19  2014 trace.c
-rw-rw-r--  1 amandalmoen amandalmoen   35938 May 19  2014 transport.c
-rw-rw-r--  1 amandalmoen amandalmoen    7008 May 19  2014 transport.h
-rw-rw-r--  1 amandalmoen amandalmoen   34792 May 19  2014 transport-helper.c
-rw-rw-r--  1 amandalmoen amandalmoen    6468 May 19  2014 tree.c
-rw-rw-r--  1 amandalmoen amandalmoen    8660 May 19  2014 tree-diff.c
-rw-rw-r--  1 amandalmoen amandalmoen     945 May 19  2014 tree.h
-rw-rw-r--  1 amandalmoen amandalmoen   22111 May 19  2014 tree-walk.c
-rw-rw-r--  1 amandalmoen amandalmoen    2239 May 19  2014 tree-walk.h
-rw-rw-r--  1 amandalmoen amandalmoen     100 May 19  2014 unimplemented.sh
-rw-rw-r--  1 amandalmoen amandalmoen    2421 May 19  2014 unix-socket.c
-rw-rw-r--  1 amandalmoen amandalmoen     158 May 19  2014 unix-socket.h
-rw-rw-r--  1 amandalmoen amandalmoen   49324 May 19  2014 unpack-trees.c
-rw-rw-r--  1 amandalmoen amandalmoen    2291 May 19  2014 unpack-trees.h
-rw-rw-r--  1 amandalmoen amandalmoen   20634 May 19  2014 upload-pack.c
-rw-rw-r--  1 amandalmoen amandalmoen    2826 May 19  2014 url.c
-rw-rw-r--  1 amandalmoen amandalmoen     492 May 19  2014 url.h
-rw-rw-r--  1 amandalmoen amandalmoen   17009 May 19  2014 urlmatch.c
-rw-rw-r--  1 amandalmoen amandalmoen    2060 May 19  2014 urlmatch.h
-rw-rw-r--  1 amandalmoen amandalmoen    3398 May 19  2014 usage.c
-rw-rw-r--  1 amandalmoen amandalmoen    9373 May 19  2014 userdiff.c
-rw-rw-r--  1 amandalmoen amandalmoen     646 May 19  2014 userdiff.h
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May 12 11:25 usr
-rw-rw-r--  1 amandalmoen amandalmoen   16763 May 19  2014 utf8.c
-rw-rw-r--  1 amandalmoen amandalmoen    1431 May 19  2014 utf8.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 23  2014 utilities
-rw-rw-r--  1 amandalmoen amandalmoen     631 May 19  2014 varint.c
-rw-rw-r--  1 amandalmoen amandalmoen     198 May 19  2014 varint.h
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 vcs-svn
-rw-rw-r--  1 amandalmoen amandalmoen     651 May 19  2014 version.c
-rw-rw-r--  1 amandalmoen amandalmoen    2183 May 19  2014 versioncmp.c
-rw-rw-r--  1 amandalmoen amandalmoen     180 May 19  2014 version.h
drwxr-xr-x  2 amandalmoen amandalmoen    4096 May  5  2014 Videos
drwxrwxr-x  3 amandalmoen amandalmoen    4096 May  5  2014 .virtualenvs
-rw-rw-r--  1 amandalmoen amandalmoen    7390 May 19  2014 walker.c
-rw-rw-r--  1 amandalmoen amandalmoen    1126 May 19  2014 walker.h
-rw-rw-r--  1 amandalmoen amandalmoen    8013 May 19  2014 wildmatch.c
-rw-rw-r--  1 amandalmoen amandalmoen     346 May 19  2014 wildmatch.h
-rw-r--r--  1 amandalmoen amandalmoen   15749 Aug  6 17:30 wireless-info.txt
-rw-rw-r--  1 amandalmoen amandalmoen     707 May 19  2014 wrap-for-bin.sh
-rw-rw-r--  1 amandalmoen amandalmoen    9983 May 19  2014 wrapper.c
-rw-rw-r--  1 amandalmoen amandalmoen    1961 May 19  2014 write_or_die.c
-rw-rw-r--  1 amandalmoen amandalmoen    9782 May 19  2014 ws.c
-rw-rw-r--  1 amandalmoen amandalmoen   44336 May 19  2014 wt-status.c
-rw-rw-r--  1 amandalmoen amandalmoen    2718 May 19  2014 wt-status.h
-rw-------  1 amandalmoen amandalmoen      65 Aug 10 16:04 .Xauthority
-rw-r--r--  1 amandalmoen amandalmoen    1601 May  5  2014 .Xdefaults
drwxrwxr-x  2 amandalmoen amandalmoen    4096 May 19  2014 xdiff
-rw-rw-r--  1 amandalmoen amandalmoen    7182 May 19  2014 xdiff-interface.c
-rw-rw-r--  1 amandalmoen amandalmoen     944 May 19  2014 xdiff-interface.h
-rw-r--r--  1 amandalmoen amandalmoen      14 May  5  2014 .xscreensaver
-rw-------  1 amandalmoen amandalmoen     190 Aug 10 16:04 .xsession-errors
-rw-------  1 amandalmoen amandalmoen     291 Aug  9 22:39 .xsession-errors.old
-rw-rw-r--  1 amandalmoen amandalmoen    6215 May 19  2014 zlib.c
```

```
3.13.0-55-generic
```

> ```

sudo apt-get autoremove
sudo apt-get update
```It would appear that the last 2 ran for me.

---

### Post by Hadaka on 2015-08-11
perhaps we fixed it?? please post
```
df -i
```
then after you post,,connect the ethernet cable and reboot
got wired and wireless now?

---

### Post by Amanda_L._Moen on 2015-08-11
```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda7      610800 549242  61558   90% /
none           213723      2 213721    1% /sys/fs/cgroup
udev           208921    517 208404    1% /dev
tmpfs          213723    578 213145    1% /run
none           213723      3 213720    1% /run/lock
none           213723     13 213710    1% /run/shm
none           213723     38 213685    1% /run/user
/dev/sda8      864960  56803 808157    7% /home
```

---

### Post by Hadaka on 2015-08-11
I still dont know why that inode count is so high on sda7
partitioning and disk space allocation are not my strong points
so i am sorry to say i cant help you with that. I would suggest
you go through and see if you can delete unused files in your home directory
and make sure nothing is open and running.I am going to do some more
research on how to clear and find what is elevating the dev/sda7 inode count
im pretty much at the apex of my knowledge on the subject. sorry i dont
have the answers at this time,I shall keep looking, thanks

ok, here is a good link to help locate and remove the excess inodes
[http://linuxcommando.blogspot.com/2008/09/how-to-find-and-delete-all-hard-links.html](http://linuxcommando.blogspot.com/2008/09/how-to-find-and-delete-all-hard-links.html)
looking at the files in your home directory tells me you have the talent to make some script
files to make it easier. It also tells me that it is more than likely the source of the problem.
Did your wired connection work after you ran the updates???

---

### Post by Amanda_L._Moen on 2015-08-11
I was downloading and running updates, and fell asleep during that. I'll check the wired network when I get home from work this afternoon. On a positive note, everything worked properly, when I started the computer I didn't have to make any other selections when the OS loaded. WiFi worked just fine! Woohoo! 

Thank you so much for your help. 

I will let you know how everything works out this evening.

---

