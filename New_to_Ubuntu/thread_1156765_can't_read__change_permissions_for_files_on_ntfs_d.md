---
title: "can't read / change permissions for files on ntfs drive"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by greenarg on 2009-05-12
Hi,
  I have an external hd (filesystem: ntfs 3.1) that was originally used with windows, then ubuntu. Somewhere along the way permissions got messy... really messy. Somehow I wound up with a folder or two full of files that I can't even read from (or copy, or edit, ...) or change their permissions - with windows or ubuntu. 

I have tried sudo chmod/chown, and the equivalent 'advanced' file ownership options in windows to try and fix the problem, to no avail. The files still say they are owned by root, but I can't access them as root.

Does anyone have a notion as to how I might get access to these files?

thanks.

---

### Post by JBA2337 on 2009-05-24
> **Ellen2 said:**
> I hope you have used the commands for setting permissions something like this:

sudo chown someusername -R * (change ownership of all files and folders to someusername)
sudo ch**mod** 777 -R * (allow read, write execute on all files and folders by everybody)

Otherwise your problem may be related to how you are mounting your external drive. Search for fstab, mounting and permissions.
For at least a week, I have been struggling with the question: how do I change the owner and the permissions of an NTFS partition? I tried several different terminal commands using chown and chmod and none of these worked. I eventually figured out a coomand that works.

In my etc/fstab file the usual boot comand for me is:
/dev/sda1 /media/Disk\040C:\040ntfs ntfs-3g  defaults,locale=en_US.UTF-8 0 0 

This command was automatically generated in the fstab file when I installed the NTFS Configuration Tool. When I boot my computer this command automatically mounts the NTFS partition on my computer.

To change the permissions and the owner of the NTFS partition, I disabled the above command, and now this is the command in etc/fstab:
/dev/sda1 /media/Disk\040C:\040ntfs ntfs-3g  defaults,umask=007,uid=1000,gid=1000,relatime        0       2

Now when I boot up my computer, root is not the owner of the NTFS partition. In  the permissions the owner and the group of the NTFS partition is now me "jim". In the permissions, for Others > Folder access it says "none". I have no idea why that happened, but it really doesn't matter as I am the only one who uses this computer.


JBA2337

---

### Post by asmoore82 on 2009-05-24
Yes, naturally NTFS cannot properly store Unix style file permissions so you have to fake them at mount time.

the ``umask=007'' part is what is forcing no access for other users,
you could change this to ``umask=002'' to force "read only" for other users.

---

### Post by zubin71 on 2009-05-24
try unmounting your drive and remounting it with the required read and write privilages....
reply if that still does not work! 
we`re here to help... :-)

---

### Post by greenarg on 2009-07-23
Ok. Thanks folks. Upgraded to Jaunty and am now just getting back to this problem. 

So, I tried the suggestion from JBA2337, with the tweak from asmoore82. Thanks folks, but no dice. 

I put into /etc/fstab the following:
> /dev/sdb1     /media/extHD     	      ntfs-3g defaults,umask=002,uid=1000,gid=1000,relatime 0 2

My hd mounts nicely (as root) and I see that the permissions on the problem files have changed to me as the owner. But... I still get > You do not have the permissions necessary to open the file. when trying to open them, either as me or as root. I can chown and chmod without apparent errors till my fingers ache, but nothing seems to do actually let me open these files. 

Ideas?

---

### Post by ddnev45 on 2009-07-23
My fstab entry looks similar to post #5 in this thread:

[HowTo Automount NTFS Drives]("http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+ntfs")

There may be some additional tricks for external drives in that thread.

---

### Post by r0g on 2009-08-25
Bump!

---

### Post by greenarg on 2009-09-29
Ok. From reading, it appears that ntfs doesn't exactly always support permissions. So I tried:
```
sudo cp -r /media/extHD/folderIwant /home/placeIwantIt/ 
```

I get all kinds of permission denied errors. Specifically:
```
cp: cannot open `/media/extHD/folderIwant/someFileIwanted' for reading: Permission denied
```. 

I'm trying to copy as sudo but get permission denied - what gives?

I'm about to give up on these files, wipe the drive, and start over. Does anyone know what is up with this?

---

### Post by facultyofmusic on 2011-01-17
The sad thing is that some of us are dual booting Windows and Ubuntu, and to some (like me) this requires a lot of experimentation with Wine.  Having to copy the executables to ext4 filesystem to be able run it is a real pain.

But why is NTFS by default locked?  I've set my fstab options to rw,exec, umask=000,dmask=000 and it still doesn't work.  Perhaps my attempts on setting fstab is futile because NTFS does not support permission fields.

---

### Post by theboxseat on 2011-01-18
As you are accessing the Hard drive on a non NTFS operating system, it is not the NTFS protections(hahaha) that you need to concern yourself with.

In linux: open a terminal window and type in: "gksudo nautilus"

This opens up a nautilus window where you have super-user privileges.

Browse to the relevant external hard-drive and open up the properties window and select the permissions tab.

Make yourself the owner and make sure that you have read and write privileges.

Also click on the tab labeled: "Apply permissions to enclosed files" that is about two thirds of the way down the pages

Job done

good luck

---

### Post by mc4man on 2011-01-18
> Having to copy the executables to ext4 filesystem to be able run it is a real pain.

But why is NTFS by default locked? I've set my fstab options to rw,exec, umask=000,dmask=000 and it still doesn't work.

This has nothing to do with permissions on .exe's whether on a ntfs or any other file system.
.exe's don't, nor ever had to have the execute bit set.

What is in play here is the default wine, (wine windows program loader), as provided in ubnutu now, uses the "cautious launcher" (security bit policy

This is what's requiring the bit set, nothing else.

Simply use wine instead.
One time setup - (among several ways to 'fix'

right click on any .exe -> open with - other application -> use a custom command
for the custom command just
wine
This will create a new right click option "wine" and can also become the d. left click default for .exe's. It will not use the cautious launcher and will not require the x bit set.

---

### Post by burntfuse on 2013-04-08
Sorry for the years-late post to an old thread, but since I ran into (and managed to solve) this problem myself with a friend's hard drive recently, and as this thread turned up as the second entry in a Google search for my problems, I thought it might be useful to leave some advice for anyone else who runs into the same problem...

Open the folder with the files giving you trouble in Windows and check if the filename is green.  If so, it means that it's encrypted using the NTFS inline encryption, which NTFS-3G doesn't support according to their website.  Windows also seems to limit what you can do with encrypted files (no copying, etc.).  Encryption being enabled was my problem, and unless something about the filesystem itself is corrupted, that's pretty much the only reason I can come up with why this would happen.  Some people here seem to be misunderstanding the original poster's situation as being the more normal problems of trying to access files as a normal user (and not having proper permissions), or having insufficient file permissions/ownership, etc., but the problem really is with not being able to **read** files even while:
[B]1. Acting as root (which alone should make it work normally)
2. The file owner already being root
3. The file owner explicitly having read permissions[/B]

Anyways, encryption can be disabled from Windows inside the file properties dialog, and if encryption's the problem then that'll fix it.

---

### Post by oldos2er on 2013-04-08
Closed, please don't bump old threads.

---

