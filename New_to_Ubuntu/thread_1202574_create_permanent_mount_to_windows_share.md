---
title: "create permanent mount to windows share"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by davedeacon on 2009-07-02
after some issues with the keyring being locked, a bit of a fight, and then a reload I am now up and running with 9.04.
Can connect to my windows vista machine to access shares but cannot make that permanent - ie create icon on desktop to take me back to the share when I log on.
Can anyone advise please ??
Many thanks, noob learning fast :)
Dave):P

---

### Post by Boondoklife on 2009-07-02
You may want to look into mounting a cifs share in your /etc/fstab file. It has been discussed on the forum many times.

---

### Post by benrb on 2009-07-02
Check this out:
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by decoherence on 2009-07-02
EDIT: try the solution at benrb's link first!

...just a question for any fellow forum-goers who might know; is the way to do this still /etc/fstab or is there a way to do it with udev?

In any case, you'll probably need some more information, such as the device name of the drive. It will be something like /dev/sdb1. To find out the exact name, put the following in a terminal (Applications > Accesories > Terminal)

```
sudo fdisk -l
```

This will give you the device names of all recognized partitions. The one you want will have "NTFS" on the line -- hopefully there's just the one!

So, lets assume you've identified /dev/sdb2 as the windows drive and you want to mount it in /media/windows. Back in the terminal type

> 
sudo cp /etc/fstab /etc/fstab.BAK
sudo nano /etc/fstab

The first command makes a backup in case something goes horribly wrong. In the screen that comes up, you'll want to add something like the following below everything else

```
/dev/sdb2 /media/windows  ntfs iocharset=utf8,umask=000    0  0
```

Now, in the file manager, you can go to /media and drag a link of 'windows' to your desktop (hint: hold down the alt key as you're dragging)

---

