---
title: "How do I label a removable disk?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2010-02-16
I feel silly for even having to ask but I don't know the answer and it doesn't seem to come up any where when I search the forums...

I just bought a 32GB SDHC SD card for my eeepc 901, running Ubuntu Hardy Heron 8.04.4 and would like to be able to label it so it displays a name when it is mounted on the desktop.  In Windows the way to do this is to right click on on the disk icon in "My Computer" and select properties, then change the name in the field provided.  Formatting also works, but I'd prefer not to have to do that as I've already began loading it up.

There does not seem to be an obvious method for doing this simple task in Ubuntu, could someone please tell me how?

Thanks in advance!

--bornagainpenguin

---

### Post by mcduck on 2010-02-16
System/Administration/Disk Utility is the tool you are looking for... ;)

(You'll need to right-click the drive and unmount it before you can edit the label)

---

### Post by bornagainpenguin on 2010-02-16
> **mcduck said:**
> System/Administration/Disk Utility is the tool you are looking for... ;)

(You'll need to right-click the drive and unmount it before you can edit the label)

Thanks!  I'll try it out once I finish the copying operating I have going on at the moment.  I knew there had to be a way, I just didn't know what it was.

--bornagainpenguin

---

### Post by ibuclaw on 2010-02-16
A more indepth page of what to do, what packages you require can also be found here:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Regards
Iain

---

### Post by mcduck on 2010-02-16
> **bornagainpenguin said:**
> Thanks!  I'll try it out once I finish the copying operating I have going on at the moment.  I knew there had to be a way, I just didn't know what it was.

--bornagainpenguin

Oh, I just noticed... If you are really running 8.04 you won't have such tool available,. In that case just use the guide ibuclaw linked.. :)

---

### Post by bornagainpenguin on 2010-02-16
> **mcduck said:**
> Oh, I just noticed... If you are really running 8.04 you won't have such tool available,. In that case just use the guide ibuclaw linked.. :)

I was going to say...

[[IMG]http://img534.imageshack.us/img534/7607/screenshotsetdisklabelo.png[/IMG]](http://img534.imageshack.us/i/screenshotsetdisklabelo.png/)

I'd really rather not format the disk brand new right out of its case!

I guess I'll have to see if I can do it another way somehow, since even the guide ibuclaw linked doesn't really seem to apply to me.

--bornagainpenguin

**EDIT--** I see now that I mistook gparted for the disk utility (which to my understanding doesn't exist in Hardy Heron 8.04.4) so what I ended up doing was booting Karmic off of a flash drive and labeling my SDHC SD disk from there.  Thanks for the help!

[http://img717.imageshack.us/img717/1926/screenshotdesktop.png](http://img717.imageshack.us/i/screenshotdesktop.png/)

PS: Why did I name it "Sexy"?  Well this [xkcd](http://www.xkcd.com/691/) ought help you there...

---

### Post by ibuclaw on 2010-02-17
> **bornagainpenguin said:**
> 
I guess I'll have to see if I can do it another way somehow, since even the guide ibuclaw linked doesn't really seem to apply to me.

--bornagainpenguin


Forgive the title of the page, and you'll see that the link applies to all filesystems specified in the guide (FAT16/FAT32, NTFS, ext2/ext3, JFS, ReiserFS, and XFS filesystems), regardless of the device it is stored on. ;)

For example, if your SD card has a Fat32 filesystem on it.
```
sudo mlabel -i <device> ::<label>
```
Would be the correct command to issue.

ie:
```
sudo mlabel -i /dev/sdc1 ::Sexy
```

But, glad you got it solved via alternate methods.

Regards
Iain

---

### Post by audiomick on 2010-02-17
> **bornagainpenguin said:**
> 
**EDIT--** I see now that I mistook gparted for the disk utility (which to my understanding doesn't exist in Hardy Heron 8.04.4) so what I ended up doing was booting Karmic off of a flash drive and labeling my SDHC SD disk from there.  Thanks for the help!

 
10 points for lateral thinking! :popcorn:

---

