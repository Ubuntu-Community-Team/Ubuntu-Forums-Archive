---
title: "Need Help Mounting a Drive"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2010-04-02
I tried to use MountManager but when I open the drive it doesn't show the files (it shows the folder in it but no files). Im trying to mount drive /dev/sda1, any help would be appreciated. I just need to mount it to add a few files and then I dont need it mounted again.

```
/dev/sda1: UUID="4c87fe42-8dca-305b-8dff-ac8b4240c4df" LABEL="EFI" TYPE="hfsplus" 
/dev/sda2: UUID="120976fb-cf43-33a3-ad51-9e6eb1b66e1b" LABEL="Macintosh HD" TYPE="hfsplus" 
/dev/sda3: LABEL="SHARED DATA" UUID="1CF3-0FF9" TYPE="vfat" 
/dev/sda4: UUID="E0D873FFD873D1F0" LABEL="Windows 7 Pro" TYPE="ntfs" 
/dev/sda5: UUID="746d7b2f-8dc1-4f77-9367-d2c2e3c09f49" TYPE="ext4" 

```

---

### Post by kaizokuroof on 2010-04-02
First you need to make a mount point for the drive.

open up a terminal an paste/type this command: 

```
sudo mkdir /dev/sda1
```That will make the mount point for you.

Then try this code:

```
sudo mount /dev/sda1
```

to unmount the drive:

```
sudo umount /dev/sda1
```

Hope this works for you, I'm still new to Ubuntu. Good luck.

---

### Post by Gone fishing on 2010-04-02
OK thats a Mac partition - isn't it?

I found this thread which suggest you may need to boot to OSX and turn off journaling [http://ubuntuforums.org/showthread.php?t=1076577&highlight=hfs](http://ubuntuforums.org/showthread.php?t=1076577&highlight=hfs)

Then I think ```
sudo mkdir /media/OSX
```

Then ```
sudo gedit /etc/fstab
``` and adding

UUID=4c87fe42-8dca-305b-8dff-ac8b4240c4df /media/OSX hfsplus ro,exec,noauto,users 0 0

would do the trick the partition should be mounted on next reboot

---

### Post by RookieUbuntuUser58 on 2010-04-02
Thanks for the help. I was able to finally mount it and replace files that needed to be replaced.

---

