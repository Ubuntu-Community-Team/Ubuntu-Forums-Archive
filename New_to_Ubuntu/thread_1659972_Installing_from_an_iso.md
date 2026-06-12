---
title: "Installing from an iso?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by tmcthree on 2011-01-04
Hi, (please be gentle with me I'm quite new)

Anyway, I'm trying to install maya from an iso.

Problem one is that the when I burn the iso onto a disk, it seems to work, but when I put the dvd on the drive after burning nothing happens.

and sudo mount -r /dev/dvd /mnt/dvd 
returns
mount: mount point /mnt/dvd does not exist


Ok so I mounted the iso instead, but then the installation instructions from the maya instruction manual dont seem to apply 

Can anyone tell me how to translate these instructions if I've directly mounbted the iso rather than the dvd please?

1 Log in as root.
2 Insert the Maya DVD into your drive.
3 Mount the DVD drive. For example, type:
4 Change to the directory where the Maya for Linux is installed. For example,
 type:
5 Use the ls command to list the packages on the DVD.
mount -r /dev/dvd /mnt/dvd
cd /mnt/dvd/Linux
Package Name Description When required
(# is the package number) 
(32-bit) AWCommon-10.80-#.i686.rpm Licensing Always
(64-bit) AWCommon-10.80-#.x86_64.rpm software 
(32-bit) Licensing For serving
         Server networked
         software licenses
Maya for Linux Always
AWCommon-server-10.80-#.i686.rpm
(64-bit)
AWCommon-server-10.80-#.x86_64.rpm
(32-bit) Maya-8.5-#.i686.rpm
(64-bit) Maya64-8.5-#.x86_64.rpm
Installation and Licensing Guide
47
5 | Installing Maya for Linux
> Installing Maya (Linux)
Package Name Description When required
(# is the package number) 
(32-bit) Maya 8.5 Optional
         documentation 
Hardware lock Only if you have
drivers for Red a hardware lock
Hat and SUSE (dongle)
Maya-docs_en_US-8.5-#.i686.rpm
(64-bit)
Maya64-docs_en_US-8.5-#.x86_64.rpm
(32-bit)
aksusbd-redhat-1.8.1-3.i386.rpm
aksusbd-suse-1.8.1-3.i386.rpm
(64-bit)
At time of release, 64-bit dongle drivers
were not available. To download them
when they become available, go to:
[www.aladdin.com/support/hasp/](www.aladdin.com/support/hasp/)
enduser.asp
6
To install the required base software, enter the following command:
(32-bit)
rpm -ivh AWCommon-10.80-1.i686.rpm Maya-8.5-#.i686.rpm
(64-bit)
rpm -ivh AWCommon-10.80-#.x86_64.rpm Maya64-8.5-#.x86_64.rpm
where # refers to the specific package numbers.
Note
If you have a previously installed version of AWCommon and Maya
for Linux, uninstall that version before installing this newest
version. To verify what version you have, type:
rpm -qa | egrep 'AWCommon|Maya'
For more information, see “Uninstalling Maya” on page 50.
Installation and Licensing Guide
48
5 | Installing Maya for Linux
> Installing Maya (Linux)
Maya 8.5 adds the required libxm.so.3 library to the Maya lib directory as
part of its standard install, so installing the openMotif runtime rpm is not
required.
7 Verify that OpenGL is installed. Look for a file named libGL.so in the /usr/
 lib or /usr/X11R6/lib directory.
8 To install the documentation package, type the following where # is the
 specific package number:
9
(32-bit) rpm -ivh Maya-docs_en_US-8.5-#.i686.rpm
(64-bit)rpm -ivh Maya64-docs_en_US-8.5-#.x86_64.rpm
If you have a hardware lock, you’ll need to install the hardware lock drivers.
You can install them by typing one of the following, depending on your Linux
distribution:
rpm -ivh aksusbd-redhat-1.8.1-3.i386.rpm
rpm -ivh aksusbd-suse-1.8.1-3.i386.rpm
You may receive an error message during installation about a missing file;
this does not affect hardware lock driver operation.
10 You should see the software files installed in the following directory:
(32-bit) /usr/aw/maya8.5
(64-bit) /usr/aw/maya8.5-x64
Once the Maya software is successfully installed, unmount and eject the DVD
and store it in a safe place. Proceed to the Licensing Maya chapter or, if
you’re a new user licensing a single copy of Maya, see the Quick Start
Licensing chapter.

---

### Post by blind2314 on 2011-01-04
You have to make the directory that you're trying to mount to before you can actually mount anything there.
```
mkdir /mnt/dvd
```

Then run your mount command and it should work just fine. If you get stuck again, post back and I'll see if i can help any more.

---

### Post by tmcthree on 2011-01-04
> **blind2314 said:**
> You have to make the directory that you're trying to mount to before you can actually mount anything there.
```
mkdir /mnt/dvd
```

Then run your mount command and it should work just fine. If you get stuck again, post back and I'll see if i can help any more.

ok now it says 
mount: you must specify the filesystem type

Are we now trying to work from the Dvd, because O don't think my computer is reading it for some reason. 

I've used "Archive mounter" so the iso is now mounted on my desktop, is it possible to work from there?

---

### Post by blind2314 on 2011-01-04
It should, depends on the install instructions for Maya. To get the DVD to mount, try to add this:

```
mount -rt iso9660 /dev/dvd /mnt/dvd
```

---

### Post by tmcthree on 2011-01-04
Thanks this seems to be working, however I now get down as far as step 6 in the above instructions. and I get this


/mnt/dvd/Maya/linux-amd64$ rpm -ivh AWCommon-server-10.80-15.x86_64.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	/bin/sh is needed by AWCommon-server-10.80-15.x86_64

---

### Post by blind2314 on 2011-01-04
ok, my best guess is that for whatever reason that script is expecting your current shell to be Bourne Shell (or dash..whatever Ubuntu uses, Bourne is a holdover from my Solaris experience) but you're currently running Bash, or at least, most likely.

Try this:

```
sh
```

Then execute the script again.

---

### Post by tmcthree on 2011-01-04
ok, do I want to run rpm as it seemed to complain about it?

---

### Post by blind2314 on 2011-01-04
That's your choice. If you want to try alien, by all means go for it.

```
sudo apt-get install alien
```

The default according to the man pages is to convert the file given to a debian package, .deb, which is what Ubuntu will expect, so you shouldn't need any flags.

---

### Post by tmcthree on 2011-01-04
> **blind2314 said:**
> That's your choice. If you want to try alien, by all means go for it.

```
sudo apt-get install alien
```

The default according to the man pages is to convert the file given to a debian package, .deb, which is what Ubuntu will expect, so you shouldn't need any flags.

ooh yeah how do I convert to a deb, I've installed them before!

---

### Post by blind2314 on 2011-01-04
By taking the default command, with no flags...at least, that's what I think.

```
alien <nameoffile>
```

That should convert it. However, if it doesn't work, I'd advise just trying to install the .rpm

---

### Post by tmcthree on 2011-01-04
ok I think its installed, the software centre seems to have done it, but how do I run it?

---

### Post by blind2314 on 2011-01-05
Well, chances are it created an icon for you in in the Application menu up top. Try that. If not, look around in /usr/bin for an executable (not an .exe obviously) that will allow you to run it.

---

