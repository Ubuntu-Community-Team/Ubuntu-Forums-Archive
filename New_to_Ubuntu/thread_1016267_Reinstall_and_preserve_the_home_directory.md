---
title: "Reinstall and preserve the home directory?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Starks on 2008-12-19
Is this possible without separate partitions?

---

### Post by taurus on 2008-12-19
Don't think so unless you just want to reinstall on top of the older version without formatting the partition first.

---

### Post by Starks on 2008-12-19
> **taurus said:**
> Don't think so unless you just want to reinstall on top of the older version without formatting the partition first.

How does one do that?

---

### Post by Michael.Godawski on 2008-12-19
> **Starks said:**
> Is this possible without separate partitions?

You can always create a separate /home partition even if you forget to do so :p


[LIST]
[*][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[/LIST]

---

### Post by taurus on 2008-12-19
When you get to the partition screen, pick Manual and have the installer mount whichever partition as / but do not put a check mark on the box regarding format.  Then, it will not format that partition.

However, is that what you really want to do, reinstalling the new version on top of the old one?  I assume you want to reinstall because there is something wrong with the current version on your harddrive.  Wouldn't it be better just to do a backup of your $HOME on a portable drive like USB first.  Then when you reinstall, create a separate partition for /home so you don't have to worry about this scenario again.

---

### Post by Starks on 2008-12-19
I've done separate partitions in the past, but usually after the installation.

It's always a pain in the ***.

---

### Post by anjilslaire on 2008-12-19
much easier to create the separate partitions during install, not after...

---

### Post by albinootje on 2008-12-19
> **Starks said:**
> Is this possible without separate partitions?

If you didn't have a separate /home partition, then this is not possible because the / partition needs to be formatted during a re-install.
Backing up /home to a usb-disk, and carefully putting it back is recommended instead.

---

### Post by markbuntu on 2008-12-19
**YOU DO NOT NEED TO REFORMAT TO REINSTALL!!!**

A reinstall will overwrite all the files it needs to and leave the rest alone including your personal data files if you do not format during a reinstall. It will also leave many application files in /bin, /usr and /etc so you will not need to download them again. But then again, if that is where the problem is.... still, you should try that first because it may work and is not so drastic as reformatting.

Intrepid has a installation recovery option on the live cd so you should try that first.

---

### Post by SuperSonic4 on 2008-12-19
I think you can use gparted to make a blank ext3 partition and then make a note of where it is (dev/sdXX)

```
sudo mv /home /dev/sdXX
``` 

try at your own peril for it's untested, mv is move

---

### Post by albinootje on 2008-12-20
> **SuperSonic4 said:**
> I think you can use gparted to make a blank ext3 partition and then make a note of where it is (dev/sdXX)

```
sudo mv /home /dev/sdXX
``` 

try at your own peril for it's untested, mv is move

Let's assume /dev/sde4 is the new extra partition where /home will end up :
This is a better way to make a backup :

```

sudo mkdir /media/temp
sudo mount /dev/sde4 /media/temp
cp -arv /home /media/temp/

```

Moving your home with mv while using your Ubuntu installation at the same time, might not even be possible.
Copying with cp is prefered.

---

