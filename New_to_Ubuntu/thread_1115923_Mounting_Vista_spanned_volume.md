---
title: "Mounting Vista spanned volume"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by blackstripes on 2009-04-04
I have two 1TB hard drives that I have converted to dynamic disks and created one 2TB spanned volume in Vista.  I am trying to access them from my Ubuntu installation without success.  One drive is on a SATA port on the mobo, and the other is connected through eSata via a JMB360 Sata PCIe controller card.

I'm not really sure where to start, the drive shows up in Nautilus, but I'm not sure if it is seeing both drives, or just the one connected to the mobo...

Can someone point me in the right direction?

---

### Post by taurus on 2009-04-04
Run this command from a terminal and see which one Ubuntu is detected.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> Run this command from a terminal and see which one Ubuntu is detected.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x718c66f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976761528+  42  SFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b62b8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48642   390710272    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29268   235095178+  83  Linux
/dev/sdc2           29269       30394     9044595    5  Extended
/dev/sdc5           29269       30394     9044563+  82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x718c66f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976761528+  42  SFS

```

Here is the output, looks like both 1TB drivers are recognized, right?  If that is the case I'm not sure why it won't mount the drives.

---

### Post by blackstripes on 2009-04-04
Here is the error message given when attempting to mount:
[IMG]http://img.photobucket.com/albums/v103/patrickz/Unabletomount.jpg[/IMG]

---

### Post by taurus on 2009-04-04
Did you shutdown windows cleanly the last time you used it?

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> Did you shutdown windows cleanly the last time you used it?

Yes I did.

I have been looking at this thread:

[http://ubuntuforums.org/showthread.php?t=763612&highlight=spanned+volume+mount](http://ubuntuforums.org/showthread.php?t=763612&highlight=spanned+volume+mount)

which references this document:

[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

but so far haven't been able to make any headway.

---

### Post by blackstripes on 2009-04-04
I am having problems getting ldminfo to work.  For some reason it is telling me that it doesn't exist:

```
patrick@Ubuntu-Desktop:~$ cd linux-ldm-0.0.8/test
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ ls
compat.c  dump.c   ldminfo    ldminfo.h  sparse.c
copy.c    extra.h  ldminfo.c  Makefile
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ ldminfo
bash: ldminfo: command not found
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ ./ldminfo --dump /dev/sda
bash: ./ldminfo: No such file or directory
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ 
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ 

```

---

### Post by taurus on 2009-04-04
What's the output of this command?

```
ls -la
```

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> What's the output of this command?

```
ls -la
```
```

patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ ls -la
total 80
drwxr-xr-x 2 patrick patrick  4096 2002-08-09 05:40 .
drwxr-xr-x 6 patrick patrick  4096 2002-08-09 05:40 ..
-rw-r--r-- 1 patrick patrick  4976 2002-08-05 10:46 compat.c
-rw-r--r-- 1 patrick patrick  2933 2002-02-23 10:38 copy.c
-rw-r--r-- 1 patrick patrick  8840 2002-06-16 20:28 dump.c
-rw-r--r-- 1 patrick patrick  1514 2002-08-05 10:46 extra.h
-rwxr-xr-x 1 patrick patrick 24076 2002-08-09 05:40 ldminfo
-rw-r--r-- 1 patrick patrick  4790 2002-08-09 05:38 ldminfo.c
-rw-r--r-- 1 patrick patrick  1184 2002-08-05 10:46 ldminfo.h
-rw-r--r-- 1 patrick patrick   602 2002-02-23 10:38 Makefile
-rw-r--r-- 1 patrick patrick  2641 2002-02-09 07:46 sparse.c
```

---

### Post by taurus on 2009-04-04
How about

```
uname -m
file ldminfo
ldd ldminfo
```

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> How about

```
uname -m
file ldminfo
ldd ldminfo
```

```
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ uname -m
x86_64
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ file ldminfo
ldminfo: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ ldd ldminfo
	not a dynamic executable
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ 

```

---

### Post by taurus on 2009-04-04
> **blackstripes said:**
> ```
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ uname -m
**[COLOR="Blue"]x86_64[/COLOR]**
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ file ldminfo
ldminfo: **[COLOR="Red"]ELF 32-bit LSB executable[/COLOR]**, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

```

That's your problem.  You are running x86_64 (64bit) but ldminfo is a 32bit binary so you won't be able to run it unless you install the 32bit library on your machine first.  Or recompile it again.

```
make
```

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> That's your problem.  You are running x86_64 (64bit) but ldminfo is a 32bit binary so you won't be able to run it unless you install the 32bit library on your machine first.  Or recompile it again.

```
make
```

That doesn't sound fun.  What is my best option? I didn't compile it to begin with, here is a snippit that the document I linked to:

> Simply extract the downloaded archive (tar xvjf linux-ldm-0.0.8.tar.bz2), go into it (cd linux-ldm-0.0.8) and change to the test directory (cd test).  You will find the precompiled (i386) ldminfo utility there.  NOTE: _You will not be able to compile this yourself easily so use the binary version!_

---

### Post by taurus on 2009-04-04
Fire up synaptic and look for ia32-libs package and install the 32bit library for your machine, [http://packages.ubuntu.com/intrepid/ia32-libs](http://packages.ubuntu.com/intrepid/ia32-libs).  Then, try to run that command again.

---

### Post by blackstripes on 2009-04-04
> **taurus said:**
> Fire up synaptic and look for ia32-libs package and install the 32bit library for your machine, [http://packages.ubuntu.com/intrepid/ia32-libs](http://packages.ubuntu.com/intrepid/ia32-libs).  Then, try to run that command again.

Thanks, those libraries allowed the command to run, but it something didn't go right:

```
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ sudo ./ldminfo --dump /dev/sda
ldm_parse_privhead(): Expected PRIVHEAD version 2.11, got 2.12. Aborting.
ldm_validate_privheads(): Cannot find PRIVHEAD 1.
Something went wrong, skipping device '/dev/sda'
patrick@Ubuntu-Desktop:~/linux-ldm-0.0.8/test$ 

```

Do I need to wipe this installation and install the 32-bit version of Ubuntu?  The only reason I chose the 64-bit version was because of my processor (Q6600).

---

### Post by blackstripes on 2009-04-04
Same thing with the Ubuntu 8.10 32-bit..

```
patrick@Ubuntu-Desktop:~/Desktop/linux-ldm-0.0.8/test$ sudo ./ldminfo --dump /dev/sdd
ldm_parse_privhead(): Expected PRIVHEAD version 2.11, got 2.12. Aborting.
ldm_validate_privheads(): Cannot find PRIVHEAD 1.
Something went wrong, skipping device '/dev/sdd'
patrick@Ubuntu-Desktop:~/Desktop/linux-ldm-0.0.8/test$ 

```

This is beggining to feel like a lost cause.#-o

---

### Post by blackstripes on 2009-04-05
Bump...any ideas?

---

### Post by lodrsc on 2009-05-16
i've solved this problem, if u need ask me in icq

---

### Post by eyalwu on 2011-02-04
Hello,
Sorry to dig this post but I need some help.
@[lodrsc]("http://ubuntuforums.org/member.php?u=833631")_, _could you post  what's the fix?

I'm stuck with that 
>  ldm_parse_privhead(): Expected PRIVHEAD version 2.11, got 2.12. Aborting. 


I'm trying to mount my spanned drives. if there's a different way to do that other than using the manual here [http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt) , let me know.
any answer would be great.

thanks[FONT=Arial][/FONT]

---

