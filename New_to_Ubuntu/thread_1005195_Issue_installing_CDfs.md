---
title: "Issue installing CDfs"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ekaqu on 2008-12-08
Hi, I am new to Linux and for the most part have not had many issues switching over till I tried to run a data dvd a friend gave me.  The cd is in CDFS format.  Since Ubuntu didn't natively support this format, I went around trying to find and install it.  I used the synaptic package manager, [http://users.elis.ugent.be/~mronsse/cdfs/download/](http://users.elis.ugent.be/~mronsse/cdfs/download/)  , and [https://launchpad.net/ubuntu/+source/cdfs-src](https://launchpad.net/ubuntu/+source/cdfs-src)  to download the cdfs-src code.

after uncompressing the files, I type "make" in the new folder and I get this
```
 david@david-desktop:~/Desktop/cdfs-src-2.6.23/cdfs-2.6.23$ make 
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.o
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c: In function ‘cdfs_fill_super’:
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c:364: error: implicit declaration of function ‘iget’
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c:364: warning: passing argument 1 of ‘d_alloc_root’ makes pointer from integer without a cast
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c: In function ‘cdfs_lookup’:
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c:462: warning: assignment makes pointer from integer without a cast
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c: At top level:
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c:544: error: unknown field ‘read_inode’ specified in initializer
/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.c:544: warning: initialization from incompatible pointer type
make[2]: *** [/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23/root.o] Error 1
make[1]: *** [_module_/home/david/Desktop/cdfs-src-2.6.23/cdfs-2.6.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```

I am not sure what I am missing, if anyone would be willing to help me out, I would appreciate it.

---

### Post by Matt Yun on 2008-12-08
When compiling software from source, you usually have to be root ie. prepend 'sudo' to your 'make' command.

Fortunately, you don't have to muck around with source compiling:  there is a cdfs package for Ubuntu:  [http://packages.ubuntu.com/hardy/misc/cdfs-src](http://packages.ubuntu.com/hardy/misc/cdfs-src)

You will have to use apt-get:

**sudo apt-get update && sudo apt-get install cdfs-src**

---

### Post by ekaqu on 2008-12-08
even if I type sudo make, the exact same error comes up. 

I ran the upgrade than install via apt-get, but mount and ubuntu are both still unable to mount cdfs disks.  Is there something more that I am missing?  

```
david@david-desktop:~$ sudo mount -t cdfs /dev/cdrom /mnt/cdrom/
mount: unknown filesystem type 'cdfs'
 
```

---

### Post by mc4man on 2008-12-08
The cdfs package is just the source code and the minimum packages you'll need to compile the module. 

I'd suggest you browse to /usr/share/doc/cdfs-src and inside will be a debian readme that *may* prove useful.

---

### Post by ekaqu on 2008-12-08
The first step the readme had was to use "m-a a-i cdfs", but when I use that it tries to build it, but fails to.  Next step (if you didnt want to do it that way) was to generate the modules DEB package and install it.  This step has me using "make-kpkg modules_image" in :/usr/src/linux-headers-2.6.27-9-generic, which gives me this error:
```
 The modules_* targets should be called from a fully configured source tree,
 and one where at least make-kpkg debian has been run

```

So I move on to the next thing the readme tells me to try, "Alternatively, if you do not want to use make-kpkg or install the
   whole kernel source, please install the essential development
   packages and the kernel-headers-x.y.z-foo-bar package for your
   kernel."

so I did ```
sudo apt-get install build-essential linux-headers-2.6.27-9-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-9-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
this step leads me to doing this:
```
/usr/src/modules/cdfs$ sudo debian/rules kdist_image KSRC=/usr/src/linux-headers-2.6.27-9-generic/ KVERS=2.6.27-9-generic
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/cdfs'
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
dh_clean
rm -f /usr/src/modules/cdfs/debian/control
rm -rf /usr/src/modules/cdfs/debian/cdfs-2.* *.o *.ko */*.o */*.ko
/usr/bin/make clean || true
make[2]: Entering directory `/usr/src/modules/cdfs'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/cdfs'
cd 2.6 && /usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/cdfs/2.6'
rm *.o *.ko .*.cmd *.mod.c *~
rm: cannot remove `*.o': No such file or directory
rm: cannot remove `*.ko': No such file or directory
rm: cannot remove `.*.cmd': No such file or directory
rm: cannot remove `*.mod.c': No such file or directory
rm: cannot remove `*~': No such file or directory
make[2]: [clean] Error 1 (ignored)
make[2]: Leaving directory `/usr/src/modules/cdfs/2.6'
cd 2.4 && /usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/cdfs/2.4'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/cdfs/2.4'
make[1]: [kdist_clean] Error 2 (ignored)
for templ in /usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst /usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst.backup /usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g ; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##//g ; s/#KDREV#//g ; s/_KDREV_//g  ' < $templ > ${templ%.modules.in}; \
  done
cd /usr/src/modules/cdfs
mkdir -p debian/cdfs-2.6.27-9-generic/lib/modules/2.6.27-9-generic/kernel/fs
cd 2.6 && make KDIR=/usr/src/linux-headers-2.6.27-9-generic/
make[2]: Entering directory `/usr/src/modules/cdfs/2.6'
make -C /usr/src/linux-headers-2.6.27-9-generic/ SUBDIRS=/usr/src/modules/cdfs/2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/cdfs/2.6/root.o
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_fill_super’:
/usr/src/modules/cdfs/2.6/root.c:364: error: implicit declaration of function ‘iget’
/usr/src/modules/cdfs/2.6/root.c:364: warning: passing argument 1 of ‘d_alloc_root’ makes pointer from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_lookup’:
/usr/src/modules/cdfs/2.6/root.c:462: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: At top level:
/usr/src/modules/cdfs/2.6/root.c:544: error: unknown field ‘read_inode’ specified in initializer
/usr/src/modules/cdfs/2.6/root.c:544: warning: initialization from incompatible pointer type
make[4]: *** [/usr/src/modules/cdfs/2.6/root.o] Error 1
make[3]: *** [_module_/usr/src/modules/cdfs/2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/cdfs/2.6'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/cdfs'
make: *** [kdist_build] Error 2

```

So since that didnt work, I moved to the next step: "If you wish to patch the cdfs module into the kernel, read the
INSTALL file and use the patch.cdfs file"

In the install, it tells me to go to try to compile the code using make, which leads me back to what was my original issue:

```
/usr/src/modules/cdfs/2.6$ sudo make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/src/modules/cdfs/2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/cdfs/2.6/root.o
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_fill_super’:
/usr/src/modules/cdfs/2.6/root.c:364: error: implicit declaration of function ‘iget’
/usr/src/modules/cdfs/2.6/root.c:364: warning: passing argument 1 of ‘d_alloc_root’ makes pointer from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_lookup’:
/usr/src/modules/cdfs/2.6/root.c:462: warning: assignment makes pointer from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: At top level:
/usr/src/modules/cdfs/2.6/root.c:544: error: unknown field ‘read_inode’ specified in initializer
/usr/src/modules/cdfs/2.6/root.c:544: warning: initialization from incompatible pointer type
make[2]: *** [/usr/src/modules/cdfs/2.6/root.o] Error 1
make[1]: *** [_module_/usr/src/modules/cdfs/2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```


I am still not sure what I am doing wrong or what I am missing, so any further advice would be much appreciated

---

### Post by mc4man on 2008-12-08
I'm not sure what the problem is for you, maybe try to remove all you've done and start fresh.

It was simple on 8.04, I have to go out, I'll try 8.10 later.

Ex. on 8.04

> doug@doug-desktop:~$ sudo m-a a-i cdfs
[sudo] password for doug: 

Updated infos about 1 packages
Getting source for kernel version: 2.6.24-22-generic
Kernel headers available in /usr/src/linux-headers-2.6.24-22-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libglib1.2ldbl liblzo1
  libevent-execflow-perl libgtk1.2 libfame-0.9 libwxgtk2.6-0 libintl-perl
  libpvm3 libxosd2 libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl
  libwxbase2.6-0 lsdvd ffmpeg libmjpegtools0c2a fping anyevent-perl
  libgtk1.2-common libevent-perl libquicktime1 libimlib2
  linux-headers-2.6.24-19 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/cdfs.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.24-22-generic KSRC=/usr/src/linux KDREV=2.6.24-22.45 kdist_image
Done with /usr/src/cdfs-2.6.24-22-generic_2.6.23-3+2.6.24-22.45_i386.deb .
dpkg -Ei /usr/src/cdfs-2.6.24-22-generic_2.6.23-3+2.6.24-22.45_i386.deb 
Selecting previously deselected package cdfs-2.6.24-22-generic.
(Reading database ... 129827 files and directories currently installed.)
Unpacking cdfs-2.6.24-22-generic (from .../cdfs-2.6.24-22-generic_2.6.23-3+2.6.24-22.45_i386.deb) ...
Setting up cdfs-2.6.24-22-generic (2.6.23-3+2.6.24-22.45) ...


> doug@doug-desktop:~$ sudo mount -t cdfs /dev/cdrom /mnt/cdrom
[sudo] password for doug: 
mount: mount point /mnt/cdrom does not exist
doug@doug-desktop:~$ sudo mkdir /mnt/cdrom
doug@doug-desktop:~$ sudo mount -t cdfs /dev/cdrom /mnt/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
doug@doug-desktop:~$ 


---

### Post by Songwind on 2008-12-08
> When compiling software from source, you usually have to be root ie. prepend 'sudo' to your 'make' command.


I don't mean to hijack here, but you don't actually need to be root to run make.  Make just compiles the software in place.  Of course, it's not normally very useful after that step.

It's the "make install" command that requires root access (so it can write the new files into /usr/bin and /usr/lib, or install new kernel modules).

---

### Post by mc4man on 2008-12-08
> I don't mean to hijack here, but you don't actually need to be root to run make

In this case I believe you need to be root ( at least in the case of running m-a a-i and possibly with some of the alternate methods

---

### Post by psusi on 2008-12-08
There is no such thing as "cdfs" format.  That software looks like a hack to mount an audio cd such that it looks like a data cd containing wav files.  Data cds use either iso9660 or udf filesystems and should mount fine out of the box.

---

### Post by mc4man on 2008-12-08
> There is no such thing as "cdfs" format. That software looks like a hack to mount an audio cd such that it looks like a data cd containing wav files. Data cds use either iso9660 or udf filesystems and should mount fine out of the box.

This is a 'limited use tool' to access certain disks, nothing that 99.99% of users would ever need.

[http://users.elis.ugent.be/~mronsse/cdfs/](http://users.elis.ugent.be/~mronsse/cdfs/)

[http://packages.ubuntu.com/hardy/misc/cdfs-src](http://packages.ubuntu.com/hardy/misc/cdfs-src)

---

### Post by ekaqu on 2008-12-09
When I type in sudo m-a a-i cdfs, I get this output:

```
david@david-desktop:~$ sudo m-a a-i cdfs

Updated infos about 1 packages
Getting source for kernel version: 2.6.27-9-generic
Kernel headers available in /usr/src/linux-headers-2.6.27-9-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/cdfs.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.27-9-generic KSRC=/usr/src/linux KDREV=2.6.27-9.19 kdist_image

```

At this point I get a prompt in the window that tries to build the files.  It ends with saying "Build of the package cdfs-src fialed!  How do you wish to proceed?"  and gives three option: View  Examine the build log file, Continue  Skip and continue with the next operation, stop  Stop processing the build commands.  Stop and continue just exit the tool and view gives this:

```

dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
dh_clean
rm -f /usr/src/modules/cdfs/debian/control
rm -rf /usr/src/modules/cdfs/debian/cdfs-2.* *.o *.ko */*.o */*.ko
/usr/bin/make clean || true 
make[1]: Entering directory `/usr/src/modules/cdfs'
make[1]: Leaving directory `/usr/src/modules/cdfs'
cd 2.6 && /usr/bin/make clean
 make[1]: Entering directory `/usr/src/modules/cdfs/2.6'
rm *.o *.ko .*.cmd *.mod.c *~
make[1]: Leaving directory `/usr/src/modules/cdfs/2.6'
cd 2.4 && /usr/bin/make clean
 make[1]: Entering directory `/usr/src/modules/cdfs/2.4'
make[1]: Leaving directory `/usr/src/modules/cdfs/2.4'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/cdfs'
dh_testdir
dh_testdir: cannot read debian/control: No such file or directory

make[1]: [kdist_clean] Error 1 (ignored)
dh_testroot
rm -f build-stamp configure-stamp
dh_clean
dh_clean: cannot read debian/control: No such file or directory

make[1]: [kdist_clean] Error 1 (ignored)
rm -f /usr/src/modules/cdfs/debian/control
rm -rf /usr/src/modules/cdfs/debian/cdfs-2.* *.o *.ko */*.o */*.ko
/usr/bin/make clean || true
make[2]: Entering directory `/usr/src/modules/cdfs'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/cdfs'
cd 2.6 && /usr/bin/make clean 
make[2]: Entering directory `/usr/src/modules/cdfs/2.6'
rm *.o *.ko .*.cmd *.mod.c *~
rm: cannot remove `*.o': No such file or directory
rm: cannot remove `*.ko': No such file or directory
rm: cannot remove `.*.cmd': No such file or directory
rm: cannot remove `*.mod.c': No such file or directory
rm: cannot remove `*~': No such file or directory
make[2]: [clean] Error 1 (ignored)
make[2]: Leaving directory `/usr/src/modules/cdfs/2.6'
cd 2.4 && /usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/cdfs/2.4'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/cdfs/2.4'
make[1]: [kdist_clean] Error 2 (ignored)
for templ in /usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst
/usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst.backup
/usr/src/modules/cdfs/debian/cdfs-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
   done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}
${templ%.modules.in}.backup 2>/dev/null || true; \ 
   sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g
; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##/2.6.27-9.19/g ;
s/#KDREV#/2.6.27-9.19/g ; s/_KDREV_/2.6.27-9.19/g  ' < $templ > 
${templ%.modules.in}; \
  done
 cd /usr/src/modules/cdfs
mkdir -p
debian/cdfs-2.6.27-9-generic/lib/modules/2.6.27-9-generic/kernel/fs
cd 2.6 && make KDIR=/usr/src/linux
make[2]: Entering directory `/usr/src/modules/cdfs/2.6'
make -C /usr/src/linux SUBDIRS=/usr/src/modules/cdfs/2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/cdfs/2.6/root.o 
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_fill_super’:
/usr/src/modules/cdfs/2.6/root.c:364: error: implicit declaration of
function ‘iget’
/usr/src/modules/cdfs/2.6/root.c:364: warning: passing argument 1 of
‘d_alloc_root’ makes pointer from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_lookup’:
/usr/src/modules/cdfs/2.6/root.c:462: warning: assignment makes pointer
from integer without a cast
/usr/src/modules/cdfs/2.6/root.c: At top level:
/usr/src/modules/cdfs/2.6/root.c:544: error: unknown field ‘read_inode’
specified in initializer
/usr/src/modules/cdfs/2.6/root.c:544: warning: initialization from
incompatible pointer type
make[4]: *** [/usr/src/modules/cdfs/2.6/root.o] Error 1
make[3]: *** [_module_/usr/src/modules/cdfs/2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [all] Error 2 
make[2]: Leaving directory `/usr/src/modules/cdfs/2.6'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/cdfs'
make: *** [kdist_build] Error 2

```

Looking at this... It looks like my first issue is why non of the methods work... So how do I get the right iget and read_inode code that the c files are looking for but unable to find?

---

### Post by Matt Yun on 2008-12-09
I'm still on Hardy 8.04 x64.  After installing cdfs-src with apt-get, I did the following:

```
root@host:~# module-assistant build cdfs
Extracting the package tarball, /usr/src/cdfs.tar.bz2, please wait...
Done with /usr/src/cdfs-2.6.24-22-generic_2.6.23-3+2.6.24-22.45_amd64.deb .
root@host:~# module-assistant install cdfs
Selecting previously deselected package cdfs-2.6.24-22-generic.
(Reading database ... 346867 files and directories currently installed.)
Unpacking cdfs-2.6.24-22-generic (from .../cdfs-2.6.24-22-generic_2.6.23-3+2.6.24-22.45_amd64.deb) ...
Setting up cdfs-2.6.24-22-generic (2.6.23-3+2.6.24-22.45) ...
```

Unfortunately, I don't have Intrepid installed, so I can't reproduce your problem.

---

### Post by ekaqu on 2008-12-11
I did a bit more research on this topic and found out that iget and read_inode were removed.  Also found that there is a patch to make cdfs's source work with this ([http://trac.tcosproject.org/browser/trunk/tcos-extra-modules/patches/cdfs-2.6.25-2-486.patch?rev=812&order=date]("http://trac.tcosproject.org/browser/trunk/tcos-extra-modules/patches/cdfs-2.6.25-2-486.patch?rev=812&order=date")).

I applied this patch and was able to compile the root.c file, which was the main block before, but now I get to this:
```
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/src/modules/cdfs/2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/cdfs/2.6/daemon.o
/usr/src/modules/cdfs/2.6/daemon.c: In function ‘kcdfsd_cleanup_thread’:
/usr/src/modules/cdfs/2.6/daemon.c:183: error: implicit declaration of function ‘kill_proc’
make[2]: *** [/usr/src/modules/cdfs/2.6/daemon.o] Error 1
make[1]: *** [_module_/usr/src/modules/cdfs/2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```

kill_proc is in the linux/kernel/signal.c file, but I am unable to find this file or signal.h (which i would prefer), so I am not sure how to get daemon to be able to use kill_proc.

Anyone have an idea how to get daemon.c to use signal?

---

### Post by mc4man on 2008-12-11
Just tried on 8.10 with the intrepid cdfs-src package, same result as you.

Did a complete removal (d. checked in /usr/src to make sure nothing left.

Then did a direct download and install of the jaunty package.

After install ran the sudo m-a a-i cdfs command, installed no problem


[http://packages.ubuntu.com/jaunty/cdfs-src](http://packages.ubuntu.com/jaunty/cdfs-src)


edit:
Did a mount to check, works fine/

---

### Post by ekaqu on 2008-12-11
Thanks so much, that did the trick!  mount now can deal with cdfs file systems! =D

---

### Post by psusi on 2008-12-11
> **ekaqu said:**
> Thanks so much, that did the trick!  mount now can deal with cdfs file systems! =D

So what does that get you other than being able to see wav files on an audio cd?

---

### Post by ekaqu on 2008-12-12
The videos a friend burnt for me.

---

### Post by zosky on 2008-12-17
i have about 30 DVDs of data burned in CDFS. i hate to say it, but winBlows XP doesnt flinch when i drop one of these in the tray. why no love for the CDFS in ubuntu ?

> **ekaqu said:**
> 
At this point I get a prompt in the window that tries to build the files. It ends with saying "Build of the package cdfs-src fialed! 


im in the same situation ekaqu... but you seem to know alot more about whats going on here. i hope you can get this sorted. 

once you do, i could write steps for others 
( that is IF you can help me understand what's going on :P )

---

### Post by mc4man on 2008-12-17
@ zosky

It's pretty simple to set and use.

If your running hardy then go 

```
sudo apt-get install cdfs-src
```

If your running intrepid then go here and do a direct download and install

[http://packages.ubuntu.com/jaunty/cdfs-src](http://packages.ubuntu.com/jaunty/cdfs-src)

then

```
sudo m-a a-i cdfs 
```

After it's installed there are several ways, here's one
Create a mount point, for instance

```
sudo mkdir /mnt/cdrom
```

then insert your cd and after the drive settles

```
sudo mount -t cdfs [COLOR="Red"]/dev/cdrom[/COLOR] /mnt/cdrom
```

Adjust red to match your drive

Then go to /mnt to find.

You could also create a mount point in /media,   Ex.

```
sudo mkdir /media/cdrom3
```

```
sudo mount -t cdfs /dev/cdrom /media/cdrom3
```


then the cd will show up on desktop.

---

