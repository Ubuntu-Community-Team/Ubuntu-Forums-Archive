---
title: "Can't access files from xp partition"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by SocoJoe87 on 2009-11-07
I installed the newest version of Ubuntu on my laptop tonight, every thing is working great. Accept I would like to access my files from the VISTA ULTIMATE side, mainly music/movies/etc etc. I have tried using "Disc Mounter" but it doesn't do anything for me, only when I put my flashdrive into the USB it pops up. On my desktop computer, running a older version of Ubuntu, it finds my harddrive and allows me to access the files. Not on the laptop, can anyone help me out in figuring out what I need to do to be able to acess the files?

Thanks in advanced.


Joe

EDIT: SORRY FOR SOME REASON I PUT XP IN THE TOPIC AND MESSAGE, I AM ACTUALLY RUNNING VISTA ULTIMATE, SORRY IF THIS CHANGES THINGS.

---

### Post by nisix on 2009-11-07
Are you running karmic? I'm also having problems with karmic auto mounting

You could try

sudo fdisk -l

Find the /dev/sd** of your windows os.

sudo mkdir /media/windows (or any other name you like)

sudo mount /dev/sd** /media/windows

Then go to /media/windows to find your xp files.

---

### Post by mvalviar on 2009-11-07
As far as I know ubuntu doesn't automatically mount partitions from an internal drive. I used ntfs configuration tool. Now my xp partition is already mounted everytime I boot.

---

### Post by patchido on 2009-11-07
there is also the possibility that you didnt turn off windows properly so you cannot mount it, you should try getting into it and shuting it down proporly

---

### Post by kansasnoob on 2009-11-07
Try installing ntfsprogs:

```
sudo apt-get install ntfsprogs
```

Then reboot.

You should then be able to copy any file or folder from Win to Ubuntu. You could also destroy Win if you're reckless with Win's system files!

---

### Post by SocoJoe87 on 2009-11-08
> **nisix said:**
> Are you running karmic? I'm also having problems with karmic auto mounting

You could try

sudo fdisk -l

Find the /dev/sd** of your windows os.

sudo mkdir /media/windows (or any other name you like)

sudo mount /dev/sd** /media/windows

Then go to /media/windows to find your xp files.

When I do the sudo mount part it says can't find /dev/sda1/media/windows in /etc/fstab or /etc/mtab

---

### Post by SocoJoe87 on 2009-11-08
I also seem to be having trouble connecting to my home network, any suggestions? I have created the wireless network with right key and still wont connect. It's 128 WEP just so you know.

EDIT: Was at work a few hours ago and connected to the open network there, but it is not even showing my home network now and won't let me connect.

---

### Post by SocoJoe87 on 2009-11-08
bump... anyone?

---

### Post by Lateralis on 2009-11-08
In order to mount, you need a space between /dev/sda1 and /media/windows.

For the record, the mount command goes a bit like this:

sudo mount <device to mount> <destination directory>


For more info, check out 

man mount
mount -h


As for your wireless problems... I'm not sure what's happening, but I'm more likely to believe that there is a problem with your home network than with Ubuntu or your hardware (especially as you can connect to your work's network).

---

### Post by SocoJoe87 on 2009-11-08
> **Lateralis said:**
> In order to mount, you need a space between /dev/sda1 and /media/windows.

For the record, the mount command goes a bit like this:

sudo mount <device to mount> <destination directory>


For more info, check out 

man mount
mount -h


As for your wireless problems... I'm not sure what's happening, but I'm more likely to believe that there is a problem with your home network than with Ubuntu or your hardware (especially as you can connect to your work's network).

Ok it's giving me this error now:

mount: /dev/sda already mounted or /media/windows busy

but when I go to /media/windows  there is nothing there.


I don't know if it's my home network, I can switch to the vista side and it works fine. The network at work is open as well, at home it's encrypted with WEP 128.

EDIT: Also to note, the network doesn't even show up in the wireless selection, don't know if that is normal or not.

---

### Post by SocoJoe87 on 2009-11-08
> **mvalviar said:**
> As far as I know ubuntu doesn't automatically mount partitions from an internal drive. I used ntfs configuration tool. Now my xp partition is already mounted everytime I boot.

i've managed to get the hdd to show up in COmputer, but when I click on it, it says:

"Internal Error: no mount object for mounted volume"

I used this page to get this far:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)


Any help on how to get the drive mounted to use? When I did the dual-boot I selected 22gb for Ubuntu to install, yet I don't see that partition?

---

