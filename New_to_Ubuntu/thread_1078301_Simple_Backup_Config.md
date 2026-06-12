---
title: "Simple Backup Config"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by lotusalive on 2009-02-23
:oops: Afraid I'll always be a beginner... :oops:    If someone can guide me, I'd appreciate knowing what I did not do correctly...  I went to Sys-Admin-Simple Backup Config...  Used Defaults, except backing up .avi and .iso files, which could be what's taking it so long...  don't know because the gui has no process length indicator...   

The problem IS:  None of my admin / processes or programs are working... Not even Office will save a doc, and Synaptics won't open: causes error:  "Failed to run /usr/sbin/synaptic as user root.  Unable to copy the user's Xauthorization file."   !!!!   

WHAT DOES THIS MEAN ? ? ?  How can I stop the backup process, (if that is what is causing this) ?


I did a restart, processes restored, don't know if I have a backup, or several, removed some things in Synaptic, but now its Terminal says: "Can't write to /usr/bin/mandb/... device is too full...  Could that be too many backups ?  How can I allay it ? ?

---

### Post by blueridgedog on 2009-02-24
I suspect your backup process filled the volume.  Run:

```
df
```

and post the output

---

### Post by lotusalive on 2009-02-25
I ran KleanSweep, to find all Dups and Back-ups, but after 20 hours it only found 565.60M, so I quit the process...  Firestarter had been crashing over the past few days, with error msg: Your Kernel does not support iptables ! ! ? ?  So I quit both programs, went to re-start, after removing all non-system dependent programs in Synaptics for /usr/bin/mandb and var/lib/cache.  Upon restart, grub only loaded to initramfs, which I don't know how to run, fix or load from...  So, I installed the live-cd, to find my old desktop is in my ntfs partition !  Saved a few things to my usb.  Then upon error msg Software db is Broken, used given command, and this is result:

ubuntu@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  perl
Suggested packages:
  perl-doc libterm-readline-gnu-perl libterm-readline-perl-perl
The following packages will be upgraded:
  perl
1 upgraded, 0 newly installed, 0 to remove and 258 not upgraded.
Need to get 0B/4540kB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 102335 files and directories currently installed.)
Preparing to replace perl 5.10.0-11.1ubuntu2 (using .../perl_5.10.0-11.1ubuntu2.2_i386.deb) ...
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.10.0-11.1ubuntu2.2_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/bin/s2p': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: failed to write status record about `libgtk2-perl' to `/var/lib/dpkg/status': No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
ubuntu@ubuntu:~$ 

Would anyone be willing to take an educated guess, fill me in, explain why this happened, if it is fixable ?  Thanks in advance to all who view.

---

### Post by lotusalive on 2009-02-25
This is result of terminal command: df, while I am on live-cd

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   511492      2000    509492   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   511492      2000    509492   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   511492         0    511492   0% /lib/init/rw
varrun                  511492       100    511392   1% /var/run
varlock                 511492         0    511492   0% /var/lock
udev                    511492      2860    508632   1% /dev
tmpfs                   511492       104    511388   1% /dev/shm
rootfs                  511492    511448        44 100% /
/dev/scd0               715592    715592         0 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                   511492        12    511480   1% /tmp
/dev/sdf1               491600    384720    106880  79% /media/USB DISK
/dev/sda6             19228276  18052612    198916  99% /media/disk
/dev/sda9             60261212    184520  57015508   1% /media/disk-1
/dev/sda8             28834716  17622436   9747556  65% /media/disk-2
ubuntu@ubuntu:~$

---

### Post by lotusalive on 2009-02-25
Update Mgr on live-cd is doing this: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

ubuntu@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
ubuntu@ubuntu:~$ su
Password: 
su: Authentication failure
ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `libgtk2-perl' to `/var/lib/dpkg/status': No space left on device
ubuntu@ubuntu:~$ 



I really would appreciate some kind of explanation, if none of this can be fixed, and especially if it can be !

---

### Post by lotusalive on 2009-02-25
I tried to fix all of this with Synaptics, from Live-cd, with Reload, Mark All Upgrades, Reload, Apply, did it twice, both times Errors resulted.

1st Error:)  E: libpam-runtime: subprocess post-installation script returned error exit status 1


2nd Error:)  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


If anyone knows how I can fix this, I'd prefer to know about it, if it can or cannot be fixed and why, than to just reinstall without understanding it.  Thanks.

---

### Post by handy on 2009-02-25
Here is a highly regarded how-to:

*_[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)_*

---

### Post by blueridgedog on 2009-02-25
sda6 appears to be near full...that may be your / during a normal boot.  I think you will need to go into sda6 and delete the results of the prior backup effort as I suspect it filled your drive.  

From a terminal,  you can:

```
sudo find /media/disk -type f -size +20000k
```

Perhaps that will help you find and remove the files so you can boot normally.

---

### Post by lotusalive on 2009-02-27
I ran gparted from Live-cd, changed / to 40Gb from 20Gb, all worked fine.  Attempting to save Install at this point, see new Thread: Aptitude, if interested...  I'll save this thread, and post to it with results, if I get it accomplished...

Results of command using Live-cd:

ubuntu@ubuntu:~$ sudo find /media/disk -type f -size +20000k
find: `/media/disk': No such file or directory
ubuntu@ubuntu:~$ sudo find /media/disk -type f -size +39000k
find: `/media/disk': No such file or directory
ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
ubuntu@ubuntu:~$

---

