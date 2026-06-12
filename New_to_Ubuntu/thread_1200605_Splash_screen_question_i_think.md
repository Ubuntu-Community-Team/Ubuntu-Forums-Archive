---
title: "Splash screen question?? i think"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by carrarin on 2009-06-30
So i installed kde 4, didn't like it and uninstalled it. 
But now when i shut down the computer i still have the kubuntu splash screen displayed. How can i change this back to the ubuntu screen. This only happens when i shut the computer down. 

Also, how do i mount drives manually. i seem to be having problems do this. 
thanks.

---

### Post by tarps87 on 2009-06-30
As far as I remember you should be able to uninstall the usplash using
```
sudo apt-get remove usplash-theme-kubuntu
```
then install the ubuntu one
```
sudo apt-get install usplash-theme-ubuntu
```

or you can install start up manager using
```
sudo apt-get install startupmanager
```

For more info on usplash you can look here
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by tarps87 on 2009-06-30
> **carrarin said:**
> Also, how do i mount drives manually. i seem to be having problems do this. 
thanks.

The general process is
```
sudo fdisk -l
```
(lower case L)
To list the attached drives/partitions

Now pick the partition you want to mount e.g. sdb1
Make a folder to mount it to
```
sudo /media/testMount
```
Now mount it
```
sudo mount /dev/sdb1 /media/testMount
```

You may need to use -t to specify the file type e.g.
```
sudo mount -t ext4 /dev/sdb1 /media/testMount
```

You can use the mount man pages to see a list of the file types
```
man mount
```

Are there any specific problems you are having?

---

### Post by carrarin on 2009-06-30
error says i must specify the filesystem type

---

### Post by Simian Man on 2009-06-30
This is why people should install the 'kde' package and *not* the 'kubuntu-desktop' package!

---

### Post by carrarin on 2009-06-30
thanks! ill remember that the next time! 
yeah... probably not gonna be a next time. 

I like gnome.

---

### Post by tarps87 on 2009-07-01
> **carrarin said:**
> error says i must specify the filesystem type

In that case there is an error reading the partition type, try using the -t option.
If it is ntfs or used with windows it is possible it has be incorrectly removed, shutdown or it could be hibernating.

What format should the drive be?

---

