---
title: "Trying to install secondary hard drive"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by voteforcondit on 2009-03-14
Im trying to install a secondary hard drive 

the drive mounts 
but when i try to copy things to the hard drive 
it says permission is denied

---

### Post by drs305 on 2009-03-14
You probably haven't made yourself the owner of the mountpoint. If it is an ext3 partition and you are using default mounting settings, run this command to set yourself as the owner. This makes you the owner of the mountpoint and everything in it. Sudo and -R are powerful commands - make sure you enter them correctly:

Change the username to your username and the mount point to the partition mount point you want ownership of.
```

sudo chown -R [COLOR="DarkRed"]yourusername:[/COLOR] /[COLOR="DarkRed"]path.to.mountpoint [/COLOR]

```
Example:  sudo chown -R john: /media/data

Edit:
You can also change permissions to allow/deny access to others. The most common is probably 755, allowing you to read/write/execute and your group and others to read/execute:
```

chmod 755 -R /path.to.mountpoint

```


Welcome to the ubuntu forums.

---

### Post by voteforcondit on 2009-03-14
um... wow. i feel like i just waisted my whole afternoon. thanks.

---

### Post by sphynx_25 on 2009-03-24
Hi *waves*

I have a similar problem and although I've tried the advice given I think I may have made a mistake with the mounting of the drive so it won't work. Basically I've managed to create a directly in the media folder which is not my drive. The drive itself is sitting happily enough on the side navigation bar in computer but I cannot copy to it or read from it and it does not have the name that I had given to it (the name that that other directory in media has).

Any assistance would be greatly appreciated,
El.

---

### Post by drs305 on 2009-03-24
sphynx_25,

Since you see the device in the left pane, it probably was auto-mounted and thus didn't mount it where you wanted. We can do this by making an entry in fstab.

If you give us the results of the following we can probably get things right. If this is an ntfs drive the easiest thing to do is install ntfs-config. It can automatically make an fstab entry once you select the device and type in the mount point...
```

sudo fdisk -l
sudo blkid # if you want UUIDs rather than device names (e.g. sdd1)
cat /etc/fstab

```

---

### Post by sphynx_25 on 2009-03-24
Thank you for the prompt reply. I ran the first and second lines and got the following.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081a95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x350a3a76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
ella@valkyrie:~$ sudo blkid #
/dev/sda1: UUID="5629525f-f857-498a-8f7c-f613c3d4ca99" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9b24c5a5-0072-4519-a687-6d3fa5b3fd93" 
/dev/sdb1: UUID="59a5de6c-e2d3-43ee-8da7-099af0b83ed2" SEC_TYPE="ext2" TYPE="ext3" 

I didn't quite follow what you meant after that, I'm completely new to Linux and not very experienced with command line. At any rate would it be possible to rephrase what you meant for me to do after that?

Thank you very much for your assistance. I really appreciate it!

---

### Post by drs305 on 2009-03-24
> **sphynx_25 said:**
> 
I didn't quite follow what you meant after that, I'm completely new to Linux and not very experienced with command line. At any rate would it be possible to rephrase what you meant for me to do after that?

The # symbol in the command indicates that what follows is a comment (and won't be acted on). In the mounting instruction file (fstab), partitions used to be designated by names such as sda1, sdb1, etc. This was fine when drives were internal and never changed. Since these are dynamically assigned at boot, with the introduction of removable drives it became possible that a drive that yesterday was called sdb today could be sdd. To prevent confusing the system, each partition can now be assigned/use a UUID, a designation that doesn't normally change. 

The "cat /etc/fstab" is a command that will type out the file contents in a terminal window. So I wanted to see your fstab contents. This is the file providing your current mounting instructions.

We can try to edit it anyway, but you will have to substitute specific information for the generic entries I supply. Anything I put in **[COLOR="DarkRed"]bold red[/COLOR]** will need to be replaced by your inputs.

If the folder you want to place the files doesn't exist, run both commands. Replace *[COLOR="DarkRed"]yourusername[/COLOR]* with your user name in both commands.  If the folder exists, run the second command but first replace the [COLOR="DarkRed"]*yourmountpoint*[/COLOR] with the mount point you already want to use:
```

sudo mkdir /media/*[COLOR="DarkRed"]yourmountpoint[/COLOR]*
sudo chown -R [COLOR="DarkRed"]*yourusername:*[/COLOR] /media/*[COLOR="DarkRed"]yourmountpoint[/COLOR]*

```
Example: sudo chown -R john: /media/data

Backup fstab and open the file for editing:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Add this line to the bottom of the file and save it. The "*[COLOR="DarkRed"]yourmountpoint[/COLOR]*" should be a folder currently existing in /media and in which you want the drive's contents to show up. For instance, /media/[COLOR="DarkRed"]*data*[/COLOR]
```

UUID=59a5de6c-e2d3-43ee-8da7-099af0b83ed2 /media/*[COLOR="DarkRed"]yourmountpoint[/COLOR]* ext3 defaults 0 2

```

Now we can try it:
```

sudo umount /dev/sdb1 # unmounts sdb1 if it is already mounted. Note the spelling.
sudo mount -a  # mounts everything in fstab, including your new entry

```
If everything is correct, no messages will appear when you run the second command. It will appear it didn't do anything, but without an error message it means sdb1 is now mounted where you want it.

Added:
Here is an excellent post by bodhi.zazen explaining fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by sphynx_25 on 2009-03-24
It was smooth sailing until I got to unmounting.

> ella@valkyrie:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
ella@valkyrie:~$ sudo mount -a
mount: mount point ext3 does not exist


Now when I go to 'computer' the second drive is no longer listed at all on the side pane.The mountpoint folder, /media/enigma, is still empty.

---

### Post by drs305 on 2009-03-24
```
UUID=59a5de6c-e2d3-43ee-8da7-099af0b83ed2 /media/enigma ext3 defaults 0 2
```
In my highlighting and coloring the inputs I reversed the mount and file type.

---

### Post by t0ddy on 2009-03-24
sudo chmod -R 777 /media/disk

where disk is the second HD that is plugged

after it you can also auto-mount the hard drive using 

sudo gedit /etc/fstab

look in wikipedia for fstab that says about mounting any kind of
hd since ntfs, vfat, until swap and temp

---

### Post by sphynx_25 on 2009-03-25
Thank you both very much for your assistance. That last set of code you gave me worked drs305 *boogie*. So very exciting.

Thanks so much!
El.

---

