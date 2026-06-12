---
title: "can't chmod +x on USB flash drive (live CD)"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by carolus on 2011-02-12
Working from a live CD, I can't run a shell script from a USB flash drive.  I can't chmod +x or chmod 777 even as root.  (The flash drive is mounted rw). If I copy the script to my root directory, then I can make it executable and run it. If I copy it back to the flash drive, it loses the executable permission.  
1) Why?
2) Is there some way I can chmod +x the script without moving it from the flash drive?

---

### Post by coffeecat on 2011-02-12
> **carolus said:**
> 1) Why?

Is the flash drive formatted FAT32? You can't chmod (or chown) files on a FAT32 filesystem (or NTFS) because Microsoft filesystems do not support Linux/Unix permissions. Ownership and permissions of FAT32 and NTFS filesystems are set globally by the mount options, therefore you cannot change individual files.

> **carolus said:**
>  2) Is there some way I can chmod +x the script without moving it from the flash drive?

Only if the drive is formatted with a Linux filesystem. **EDIT**: Or mounted with the 'exec' option, but that would make everything on the drive executable.

---

### Post by carolus on 2011-02-12
> **coffeecat said:**
> Ownership and permissions of FAT32 and NTFS filesystems are set globally by the mount options, therefore you cannot change individual files.


Thanks, that's the key.  To make the script executable, I ran "mount /media/'MINI TD' -remount,exec". Then I also had to change the extension to .exe for the script itself.

Incidentally, this behavior is different from Debian, Fedora, Knoppix, Scientific Linux, and Puppy Linux, which all do a reasonable mapping of Windows permissions to Linux permissions.  (Cygwin, Red Hat's Linux emulator, also does a nice mapping.  I use it on NTFS filesystems to avoid fooling with Windows permissions.)

---

### Post by coffeecat on 2011-02-13
> **carolus said:**
> Incidentally, this behavior is different from Debian, Fedora, Knoppix, Scientific Linux, and Puppy Linux, which all do a reasonable mapping of Windows permissions to Linux permissions.  (Cygwin, Red Hat's Linux emulator, also does a nice mapping.  I use it on NTFS filesystems to avoid fooling with Windows permissions.)

Do you mean all those distros mount FAT32/NTFS volumes with the exec option? Ubuntu used to mount NTFS with exec (I can't remember what happened with FAT32) a couple of releases ago and that simply resulted in many threads being posted to this forum by people bewildered and annoyed because  their NTFS files were all executable. It seems the poor devs can't win! #-o

:wink:

---

### Post by Morbius1 on 2011-02-13
Debian will mount an external USB NTFS formatted storage device with directories at 700 and files at 600 so I don't think we can blame the Ubuntu developers on this one :)

---

### Post by carolus on 2011-02-13
> **coffeecat said:**
> Do you mean all those distros mount FAT32/NTFS volumes with the exec option? 

I mean that on all of those distros I have run shell scripts from a FAT-formatted a USB drive with never any problems, so I never discovered the "exec" option before now.

With debian-live 6.0, "mount /dev/sda1 /media/usb1", followed by "mount" shows "/dev/sda1 on /media/usb1 type vfat (rw)" (Neither exec nor noexec is listed.) "ls -l" shows execute permissions for all files on the flash drive, and chmod -x fails.  So evidently the debian default is the opposite from ubuntu. Too much permission is less noticeable than too little, and I never noticed this with the other distros. 

I use the cygwin linux emulator routinely (crunching numbers with gfortran) but only occasionally do I use a true linux system.  In most cases the emulation is very close, but cygwin seems to do a better job of emulating linux file permissions on FAT and NTFS than true linux does. chmod, chown, and ls -l work as expected.  I think the same was true of the MKS Toolkit, another unix emulator, but I haven't used that for years.

---

### Post by carolus on 2011-02-15
> **carolus said:**
> cygwin seems to do a better job of emulating linux file permissions on FAT and NTFS than true linux does. chmod, chown, and ls -l work as expected.  


My error.  I started wondering how that worked, and found that "On FAT or FAT32 filesystems, files are always readable, and Cygwin uses the DOS read-only attribute to determine if they are writable. Files are considered to be executable if the filename ends with .bat, .com or .exe, or if its content starts with #!. Consequently chmod can only affect the "w" mode, it silently ignores actions involving the other modes."  

It would be nice if linux, too, recognized leading #! as executable with the "showexec" mount option. Since I start scripts with #!/bin/sh in order to ensure portable use of the posix shell, I never noticed that this was a requirement for Cygwin on FAT.

---

### Post by Sylchat on 2011-03-15
Hi, 

I noticed that on my NTFS usb harddisk, my backup script was no longer in 'execute' permission after migrating to 10.10 since 10.04 (and chmod u+x doesn't work).

Yep, before it did work... double-click > Run, and my backup was started...

I guess this is time to convert my backup hard disk to the linux world ;)

---

### Post by carolus on 2011-03-18
> **Sylchat said:**
> Hi, 

I noticed that on my NTFS usb harddisk, my backup script was no longer in 'execute' permission after migrating to 10.10 since 10.04 (and chmod u+x doesn't work).

Yep, before it did work... double-click > Run, and my backup was started...

I guess this is time to convert my backup hard disk to the linux world ;)

Or switch to debian, which has the opposite default.  I'd rather  have too much permission than too little.

---

