---
title: "disk defragmentation and disk cleanup"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by abhigyan91 on 2009-02-22
hey every1...
how do u defragment and clean up your disks in linux? windows is quite easy.. but i dont know how to do it in linux...
also.. i thought i could defragment my ubuntu drive frm vista itself but for sum reason.. the linux drive doesn't even show up!! is ther sumtin i can do about that?

---

### Post by taurus on 2009-02-22
You don't need either one.

---

### Post by konqueror7 on 2009-02-22
every 25 times you boot your linux box, it will automatically check your drive for errors and such...so don't have to worry,,,leave your windows habits behind, this is linux...;)

---

### Post by abhigyan91 on 2009-02-22
nice...linux rox in that case.. lol

---

### Post by Crafty Kisses on 2009-02-22
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

---

### Post by mcduck on 2009-02-22
Just to elaborate a bit on the above, running "sudo apt-get clean" removes package files that Ubuntu's package manager has stored in it's cache when installing programs. Doing this will free some disk space.

---

### Post by Bradtek on 2009-02-22
The Linux drive does not show up in Windows because windows can not read the ext2 / ext3 file system used by Linux without installing a 3rd party driver.

Ubuntu Linux can read the Windows NTFS or FAT32 file system by default

---

### Post by k3lt01 on 2009-02-22
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=140920"), it should give you some tips for cleaning up. As for defragmenting, like the others have said its not required.

---

### Post by binbash on 2009-02-22
you can clean ubuntu with BleachBit (google it)

---

### Post by cerpin on 2009-02-22
> **abhigyan91 said:**
> nice...linux rox in that case.. lol


Just another reason to love Linux/Ubuntu. It took a bit getting used to for me but its great not having to run defrag programs, anti-virus', or anti spyware all the time. 


YES!

---

### Post by pacificflows on 2009-03-14
> **abhigyan91 said:**
> nice...linux rox in that case.. lol

Linux DOES rox. Do what I did, man. Give Windows the bird, and let Linux take up all of your hard drive space. Resistance is futile.

:P

---

### Post by sp176 on 2009-03-18
How about an external hard drive?  Most of the files were placed on the drive from my use in Windows.

---

### Post by TheUnderTaker on 2009-03-18
Its really more to the linux filesystems. Ext2/3/4 jfs xfs all are good at reducing fragmentation as there block allocation policys are better than NTFS and fat32.

---

### Post by SunnyRabbiera on 2009-03-22
> **sp176 said:**
> How about an external hard drive?  Most of the files were placed on the drive from my use in Windows.

External drives will probably need defragging, most external drives use NTFS or Fat32.
If you plan on ditching windows its best just to reformat your external to a linux filesystem such as ext3.

---

### Post by bapoumba on 2009-03-22
4 off topic posts removed.

---

### Post by Friedel on 2009-03-29
I have around 20,000 Pics in my home-directory, when i delete them, i HAVE to defrag...

So - how?

---

