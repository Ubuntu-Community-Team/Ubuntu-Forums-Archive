---
title: "How to keep HDD mounted thru restart?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by bettyhills on 2010-02-02
I installed a second (slave) HDD into an Ubuntu PC.  Each time I turn it on, the drive needs to be mounted.  

What (exact steps) do I need to do so that the drive stays mounted after the PC is turned off. 

The goal:  When the PC is turned on, I'd like the HDD already mounted and ready to use.

TIA

---

### Post by samantha_ on 2010-02-02
depends on which file system your using.
If your using ntfs, you can use ntfs-config (which is really easy...)
or if your using something other than that, your going to have to dwelve into the wonders of [/etc/fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by bettyhills on 2010-02-02
The master drive containing the linux system is Fat32.  It appears to be mounted and stays mounted thru a restart.  

The new slave drive is ntfs is not mounted and needs mounting after every restart.

Can you give exact step by step instructions on how to get the slave drive to stay mounted thru a restart?

---

### Post by semi_fiction on 2010-02-02
See my super old thread for help: 

[http://ubuntuforums.org/showthread.php?t=1039892](http://ubuntuforums.org/showthread.php?t=1039892)

---

### Post by snkiz on 2010-02-02
hang on you put linux on a FAT32 drive? I gotta ask why?

---

### Post by nhasian on 2010-02-03
> **snkiz said:**
> hang on you put linux on a FAT32 drive? I gotta ask why?

he probably means that he had windows on a fat32 partition and he used wubi to install ubuntu.  its probably the defualt ext4 partition if he's using karmic.

---

### Post by Shark_AtK12 on 2010-02-03
Did this earlier today with my NTFS partition to share media with winxp. Get and install ntfs-config. Then in the terminal type ntfs-config and it should pop up with a menu having you select the partitions you want. Select the ones you want to automount and make sure that write access is enabled(i think it says internal drives).

---

### Post by baddnady23 on 2010-02-03
Post the results of:

```
cd /etc
sudo gedit fstab
```

---

### Post by bettyhills on 2010-02-03
Of course, you are all absolutely correct, the master drive is default-formatted for Ubuntu, not Fat32.   My apologies.  I've lived with MS too long.

The slave drive is named "Public."
The last line in the fstab file reads:
/dev/sdb1 /media/Public ntfs-3g defaults,locale=en_US.UTF-8 0 0

The system seems to have added it for me through ntfs-config.  Restarts demonstrate that the slave drive mount persists.  The problem is solved.  Thank you all.

---

### Post by nhasian on 2010-02-03
you only need sudo if you want to make changes to the file, which can be dangerous if not backed up first.  so you can leave that off.  even better way to get the info would be

```
cat /etc/fstab
```

> **baddnady23 said:**
> Post the results of:

```
cd /etc
sudo gedit fstab
```

---

