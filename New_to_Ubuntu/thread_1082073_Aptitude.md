---
title: "Aptitude"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by lotusalive on 2009-02-27
don't laugh... attempting to learn... and maybe accomplish saving my install...  

Attempting to use Aptitude from Live-cd to fix broken system boot, that leaves me at command line initramfs, but don't know how to use that commandline.  Not sure order of operations in Aptitude to work on following problems:  

(I re-made / partition from 20Gb to 40Gb using gparted, from Live-cd and all worked.)  

Sys boot says it has missing modules: cat /proc/modules and ls/dev...

From previous fumbling around in Live-cd, used Update Mgr on prompt at panel, caused #padding for dpkg.  Currently, ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

Not sure if I have Synaptics configured properly, since Aptitude has 'Forget new packages' from an earlier choice I made.

Would someone be willing to take a stab at where I should begin to untangle my own mess ?   Thx in advance.

---

### Post by Peter09 on 2009-02-27
> dpkg: status database area is locked by another process
is due to having more than one aptitude process running at the same time.

---

### Post by lotusalive on 2009-02-27
I never started any process with Aptitude yet, was just looking...as far as I know...  Wait ? Reboot ?

---

### Post by giarca on 2009-02-27
Check with ```
ps xa|grep aptitude
``` and if there is another aptitude process kill it with ```
kill -9 NUMBEROFPROCESS
```.

If no aptitude process exist check with the first command also dpkg and other package manager.

---

### Post by Peter09 on 2009-02-27
May need a reboot if the lockfile is still locked.

---

### Post by lotusalive on 2009-02-27
Re-booted.  Am currently at process Synaptics-Reload-Mark All Upgrades, Results were:

End of Syn Upgrade: Not all changes and updates succeeded:

Unpacking replacement libstdc++6 ...
Processing triggers for man-db ...
dpkg: failed to writes status record about 'pulseaudio' to '/var/lib/dpkg/status
: No space left on device.
E: Sub-process usr/bin/dpkg an error code (2)
A package failed to install.  Trying to recover:

END DETAILS, plus, following Error Msg:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


Command in terminal results in: 

ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up cpp-4.3 (4.3.2-1ubuntu12) ...
Setting up perl-modules (5.10.0-11.1ubuntu2.2) ...
Setting up linux-libc-dev (2.6.27-11.27) ...
Setting up libc6-i686 (2.8~20080505-0ubuntu9) ...
Setting up libstdc++6 (4.3.2-1ubuntu12) ...
Setting up libgomp1 (4.3.2-1ubuntu12) ...
Setting up libc6-dev (2.8~20080505-0ubuntu9) ...
Setting up gcc-4.3 (4.3.2-1ubuntu12) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ 


Thank you for previous advising.  Will look at it to see if I am anywhere near it, lol.  Thanks.

Apparently, all reboots on Live-cd still result in 'locked-file.'  Repartition from 20Gb to 40Gb  of / did not halt error: No space left on device...

---

### Post by lotusalive on 2009-02-27
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ ps xa|grep aptitude
ubuntu@ubuntu:~$ 
  

or is this my error ?  have not initiated command beneath it yet, should i ?

---

### Post by egalvan on 2009-02-27
> **lotusalive said:**
>   

**Attempting to use Aptitude from Live-cd to fix broken system boot,** that leaves me at command line initramfs, but don't know how to use that commandline.  Not suro 40Gb using gparted, from Live-cd

Is this possible?

Can one run Aptitude (or any other package manager) from the LiveCD and fix/update the installed system?

My knowledge doesn't extend that far.

---

### Post by llamabr on 2009-02-27
Running aptitude will add content to the currently mounted os, in this case, the livecd.  It will not fix your natively mounted os.

You had a "no space left on device" error.  Post the output of df -h

---

### Post by Peter09 on 2009-02-27
A CD will always show as having no space, it will be mounted read only.

---

### Post by lotusalive on 2009-02-27
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  104K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  497M   1% /dev
tmpfs                 500M  104K  500M   1% /dev/shm
rootfs                500M  500M     0 100% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 500M   28K  500M   1% /tmp
/dev/sdf1             481M  380M  101M  80% /media/USB DISK
ubuntu@ubuntu:~$


So, any way to fix device with Live-cd ?   Or what is point of having any access  ?  (not to be rude, don't mind stupid me...lol)

---

### Post by oldos2er on 2009-02-27
> **lotusalive said:**
> ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  104K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  497M   1% /dev
tmpfs                 500M  104K  500M   1% /dev/shm
rootfs                500M  500M     0 100% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 500M   28K  500M   1% /tmp
/dev/sdf1             481M  380M  101M  80% /media/USB DISK
ubuntu@ubuntu:~$


So, any way to fix device with Live-cd ?   Or what is point of having any access  ?  (not to be rude, don't mind stupid me...lol)

 The above is info on the LiveCD. We need info on your hard disk(s). Can you boot into recovery mode?

---

### Post by lotusalive on 2009-02-28
From the Live-cd, Boot Options: recovery mode, gives me the (initframfs) and I tried the suggested commands: cat /proc/cmdline, which seems to find the uuid, one number different from the original it was looking for on boot... ie 8372, now 8472, if that means anything.  I also tried Check root and the other offered Check rootdelay command, both resulting in /usr/bin not found.

So, here I am in Safe Graphics Mode.  Don't know what the choices under F6 represent, or if they are useful to me:  acpi=off, noapic, nolapic, edd=on, Free software only, so I chose nothing.

Also offered on Live-cd under Boot Options:  file=cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash,   but that probably has nothing to do with my hard drive...

Other suggestion for Recovery Mode Boot ?  I'll go try the df -h command there and bring the results.


On that try from Live-cd, Boot Options, when I tried 'recovery mode,' instead of the (initramfs) prompt, I got a page ending in about the following 6 lines:

BIOS EDD facility v0.162004-Jun-25, 0 devices found
EDD information not available.
input: AT translated set 2 keyboard as /devices/platform/i8042/serio)/input/input1
VFS: Cannot open root device "<NULL>" or unknown-block (8,1)
Please append a correct "root=" boot option; here are available partitions:
Kernel panic - not syncing: VFS :Unable to mount root fs on unknown-block (8,1)

(end msg)

It seems my linux installs have never Upgraded in Synaptics nor Updated with Update Manager properly, nor completely... always Error Msgs as stated above...

All suggestions appreciated.  Thx.

---

