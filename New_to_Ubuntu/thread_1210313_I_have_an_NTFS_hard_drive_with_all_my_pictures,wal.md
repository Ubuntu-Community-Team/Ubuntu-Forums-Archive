---
title: "I have an NTFS hard drive with all my pictures,wallpapers etc on it and.. when I.."
date: 2009-07-11
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-11
I have an NTFS hard drive with all my pictures,wallpapers etc on it and.. when I start windows, the drive doesn't load and my wallpaper is default, untill I goto places and click the drive, how can I make the drive run at startup and never turn off?

---

### Post by Troll_the_Great on 2009-07-11
Install ntfs-config, and your drive will automount on start-up.Open a terminal (Applications - Accessories - Terminal) and type:
```
sudo apt-get install ntfs-config
``` 
After you install it, you can find it under Applications - System Tools. Run it and configure what drives do you want to automount on start-up. Post back if you have any troubles.
Cheers!

---

### Post by bodyharvester on 2009-07-11
> **FoxFireX said:**
> I have an NTFS hard drive with all my pictures,wallpapers etc on it and.. when I start windows, the drive doesn't load and my wallpaper is default, untill I goto places and click the drive, how can I make the drive run at startup and never turn off?

is it an external drive?  SSD or HDD? i dont know if that is possible, there is a way to alter the applications at startup. SYSTEM>PREFERENCES>START UP APPLICATIONS

---

### Post by FoxFireX on 2009-07-11
Internal HDD, and thanks.

---

### Post by NESFreak on 2009-07-11
this is because its not mounted at boot. It only mounts when you click onits icon.

To mount it at boot have a look here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

basically for your ntfs disk do this:

open a terminal and type
```
sudo blkid
```
this should give you a list of all your partitions and their labels

you should no which one to pick based upon its label (and filesystem)

next type:
```
sudo gedit /etc/fstab
```

add the following line and save:
```
UUID=YOURUUID /YOUR/MOUNTPOINT        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

where YOURUUID is the one you found with the previous command, and /YOUR/MOUNTPOINT is where you want the disk to appear. this probably is something like /media/windows if this directory doesn't exists yet you could create it with:
```
sudo mkdir /media/windows
```

there might be something graphical for this, but i prefer it this way.

---

### Post by Troll_the_Great on 2009-07-11
> **NESFreak said:**
> there might be something graphical for this, but i prefer it this way.

Yes, there is the NTFS configuration tool I told him about. It thought it was easier for beginners to have a graphical way to do it.
Anyway, great how-to, so he can pick any solution he likes.
Cheers!

---

### Post by FoxFireX on 2009-07-11
Graphical ftw, thanks guys.

---

