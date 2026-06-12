---
title: "Kernel Update - now cannot start"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by KB9VGD on 2009-12-06
I have a dual boot Dell with Win XP and Ubuntu 9.10. I just did the upgrade to the newest kernel update and rebooted like it wanted too. I get my menu for either Windows XP or Ubuntu and I hightlight Ubuntu and press enter. From there I get a command prompt sh:grub>. What do I have to do to get this back anf running again? I DON'T want to lose everything I had on my desktop again. This happened a while back when I did the Grub update and it screwed everything up, I ended up reloading Ubuntu and losing eveything in my mail and desktop.

Thanks for ANY help on this, I'm not too happy right now.

Gary

---

### Post by The Cog on 2009-12-06
You could try this procedure to reinstall grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would be inclined to take a backup of /home to a USB drive first though, just to be on the safe side. Boot the Ubuntu live/installer CD and choose to try without installing. Then plug in your USB disk and watch it apppear on the desktop. Then go to Places and mount the installed Ubuntu partition.

If you do **ls /media**, you should see the directories where they are both mounted. You need to figure out which directory is which disk/partition, then using the appropriate directory names, make a tar backup of the home directories like this:
```
cd /media/harddisk
sudo tar cvf /media/usbdsk/home.tar home
```
Now you can afford to experiment with replacing GRUB, or even reinstalling Ubuntu entirely.
After a reinstall, this should restore home directory: Log in to Ubuntu (no need for the live CD). Insert the USB disk and use these commands to extract the tar file:
```
cd /
sudo tar xvf /media/usbdisk/home.tar
```

---

### Post by shadowlands on 2009-12-06
I am having the same problem with my double booting system.

Can you make the directions a bit simpler ? I am doing what u ask but not understanding why I am doing it, thus, making it hard to understand what I am doing.

---

### Post by KB9VGD on 2009-12-06
I forgot to mention also that I had installed Ubuntu through windows using the Wubi installer. I'm thinking might might have been a poor decision.

Gary

---

### Post by The Cog on 2009-12-06
@KB9VGD:
That might make things trickier, but it may well still be possible to take a backup. Boot the installer CD and go to Places, then click the windows partition to mount it. It should appear in /media - perhaps /media/disk. If you can find the file that wubi uses as its virtual disk, you might be able to mount it with commands like this - I assume for the example that the virtual file is C:\wubi\virtualdisk but I have no idea what it is really called:
```
sudo mkdir /media/wubidisk
sudo mount -o loop -o umask=0 /media/disk/wubi/virtualdisk /media/wubidisk
```
after which you should be able to see the contents of the virtual disk in /media/wubidisk and then take a backup to an external USB disk as before:
```
cd /media/wubidisk
sudo tar cvf /media/usbdsk/home.tar home
```

@shadowlands:
If you boot the installer CD into the live Ubuntu system, under Places you should see all the available partitions. Double-clicking one will then mount it so you can see the contents. Doing this actually creates a folder in /media, for instance /media/disk, and you can see the contents in there. For instance, I list the contents of /media and see this:
> steve@dingly:~$ ls /media
cdrom  cdrom0
but if I then go to Places and click "21G media" a new folder appears:
> steve@dingly:~$ ls /media
cdrom  cdrom0  f00b4cfc-e4ed-4fa7-a9bb-6fc2c86f9f10
Once you can see the contents of the disk that you want to backup, you need to insert the external USB disk to make the backup to. Inserting a USB disk will make yet another folder appear in /media with the contents of the USB disk in it. What we need to do is make a tar file (a bit like a zip file) in the USB disk that contains the contents of the /home directory you are trying to back up. In my case I labeled my USB disk so it appears as /media/BACKUP. So now you need to change to the disk you want to back up: ```
cd /media/f00b4cfc-e4ed-4fa7-a9bb-6fc2c86f9f10
``` and use the tar command to back up the home folder to a tar file on the USB disk:
```
sudo tar cfv /media/BACKUP/myBackup.tar home
```

---

