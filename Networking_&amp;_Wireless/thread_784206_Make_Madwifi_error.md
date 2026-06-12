---
title: "Make Madwifi error"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by The346L3 on 2008-05-06
I installed Ubuntu onto my laptop cause windows was acting up. I tried making madwifi but this happened.
```
fong@fong-laptop:~$ make --directory=/home/fong/madwifi-0.9.4
make: Entering directory `/home/fong/madwifi-0.9.4'
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/fong/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  HOSTCC  /home/fong/madwifi-0.9.4/ath_hal/uudecode
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/fong/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/fong/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/fong/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/fong/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
make: Leaving directory `/home/fong/madwifi-0.9.4'


```

What should I do? Also how can I get vlc, music and video codecs onto my laptop without a direct internet connection? Is there anyplace I can download them and transfer it to my laptop?

---

### Post by chili555 on 2008-05-06
You should open Synaptic (System -> Administration -> Synaptic) and go to Settings -> Repositories and add the CD to your repositories. You do still have your installation CD handy, right?

Press reload and search for and install *build-essential* and *linux-headers* matching your kernel version, which, in your case, is 2.6.24-16-generic. If this is already installed, that is, the little box is green, instead of white, skip the headers, obviously.

Build-essential will want a few dependencies which you should accept. Then cd /home/fong/madwifi-0.9.4 and run 'make' again. Let us know if you get stuck again.

---

### Post by The346L3 on 2008-05-06
I had to use a virtual drive to install ubuntu cause my cd drive is broken. Since I couldnt use my windows back cds I installed ubuntu. Can I use virtual drives with ubuntu? Cause I still have the iso.

---

### Post by chili555 on 2008-05-06
You have gone way beyond my sphere of knowledge. You may be able to mount the .iso as a loop device: [http://www.linuxhelp.net/linux_downloads/](http://www.linuxhelp.net/linux_downloads/) What they glossed over here is that you must first ```
cd /mnt
sudo mkdir iso
```Then, with a little work with the Synaptic repositories, you may be able to add /mnt/iso as a repo. Then you can get build-essential and headers, if needed, do madwifi and once you are on line, go to Newegg and order a new CD drive!

If you can't add /mnt/iso as a repository, you can certainly see the packages you want to install and do:```
sudo dpkg -i /mnt/iso/folder/location/build-essential-blah-blah
```

---

### Post by The346L3 on 2008-05-07
I couldnt mount the iso, this happened
```
fong@fong-laptop:~$ cd /mnt
fong@fong-laptop:/mnt$ sudo mkdir iso
mkdir: cannot create directory `iso': File exists
fong@fong-laptop:/mnt$ mount -o loop -t iso9660 /home/fong/ubuntu-8.04-desktop-i386.iso /mnt/iso
mount: only root can do that
fong@fong-laptop:/mnt$ 

```

Also since I dont think Im gonna get the internet working on my laptop anytime soon, is there anywhere I can download video and music codecs and transfer them to my laptop?

---

### Post by chili555 on 2008-05-07
Don't give up now, when you are so close! > only root can do thatThat's asking you to run the command as 'sudo.'```
**sudo** mount -o loop -t iso9660 /home/fong/ubuntu-8.04-desktop-i386.iso /mnt/iso
```You can download anything you want at [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

---

### Post by The346L3 on 2008-05-10
I tried to mount as sudo and this happened
```
fong@fong-laptop:~$ cd /mnt
fong@fong-laptop:/mnt$ sudo mount -o loop -t /home/fong/ubuntu-8.04-desktop-i386.iso /mnt/iso
[sudo] password for fong: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
fong@fong-laptop:/mnt$ 


```

I looked at the hardy packages but I couldnt find the video and music codecs. I was also wondering if I could download madwifi without having to "compile/make" it and just have it install itself for me. If not Ill keep trying cause I think I am close, its just that its frustrating.](*,)

---

### Post by chili555 on 2008-05-11
You typed:> fong@fong-laptop:/mnt$ sudo mount -o loop -t /home/fong/ubuntu-8.04-desktop-i386.iso /mnt/isoHowever, the link I referred you to includes the file type iso9660. So please amend your command to:> fong@fong-laptop:/mnt$ sudo mount -o loop -t **iso9660** /home/fong/ubuntu-8.04-desktop-i386.iso /mnt/isoThe complaints you got boil down to 'filetype, please?'> I was also wondering if I could download madwifi without having to "compile/make"This is included in *linux-restricted-modules* which you will find on the install disc you are about to mount. Be sure to install the version matching your running kernel, which you can find with the command:```
uname -r
```

---

### Post by The346L3 on 2008-05-13
I finally got the iso mounted. Im not sure how to add .mnt/iso as a resposatory though. It asks for an apt line in the third-party software section.

Also when I tried to install the build essential the package install said the status was in "ERROR: Dependency is not satisfiable: libc6-dev libc-dev" there should be a straight line up and down between dev and lib.

---

### Post by chili555 on 2008-05-14
I'm not sure how you could add the iso as a repository; it seems like it would be easier to look around in the folders you have in /mnt/iso and simply right click the packages you want and select 'Install with GDebi Package Installer.'

If you do that with *build-essential* it will complain about all the things it needs. Simply install them one-by-one. I think, at least. you will need:```
libc6-dev 
gcc (>= 4:4.1.1)
g++ (>= 4:4.1.1)
make
dpkg-dev (>= 1.13.5)
```You may see a couple of versions of these in your .iso, you want the one that is the version mentioned, 4:4.1.1, or greater, for example. Start by installing those and *build-essential* should not have very many complaints left.

---

### Post by The346L3 on 2008-05-15
I have run into a strange problem where g++-4.2 and libstdc++6-4.2-dev each have a dependency on each other. What do I do?

---

### Post by chili555 on 2008-05-15
cd to the folder where they live: /mnt/iso/some/folder/ and then try:```
sudo dpkg -i g+++whatever.deb libstdcwhatever.deb 
```In other words, hit two debs with one stone. Let us know.

---

