---
title: "hdd external drive"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by hduguay on 2009-10-28
I have  a 500gb seagate freeagent external hdd. Which I need to reformat. Any ideas how to do this as all info on the drive seem to be windows based.

---

### Post by martrn on 2009-10-28
I have no idea what operating system you are using, no idea what operating system you wish to use sun os/mac os/ gnu linux / or something else.

If you want to partition / format and organise your external hard drive there is a tool called gparted ( [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") ), which you can download and burn to a cdrom.  When you boot gparted_livecd up you will be able to format partition and manage your external drive and read/write and view files systems of many different types.

If you are using ubuntu you can :

```
sudo apt-get install gparted
sudo gparted
```
to run the gparted application.

---

### Post by kayvortex on 2009-10-28
*If* you want to format as ntfs, you will also need the ntfsprogs package:
```
sudo aptitude install ntfsprogs
```

Once you start up gparted, select the external hdd at the top right, right-click the partition and select "unmount", and then right-click on the partition again and select "format to" and choose what you want it formatted to.

Note: I'm sure you know this already, but just in case -- formatting the disk will permanently erase all files and data on it, so be careful.

---

### Post by hduguay on 2009-10-28
I am using 9.04 ubuntu

---

