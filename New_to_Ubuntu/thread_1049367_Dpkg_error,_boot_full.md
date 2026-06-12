---
title: "Dpkg error, boot full"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by UWCAC on 2009-01-24
I'm having some problems with running updates. I get the error message: dpkg was interrupted, must manually run dpkg --configure -a to correct problem. 

When I run sudo dpkg..., I get another error that there is no space in my boot folder. I have partitions, so I tried to use the Synaptic Package Manager to fix this, but I once again got the first message that I must run dpkg --configure -a.  

To try to work around this I went into the terminal, typed sudo nautilus and cleared old files  (config., abi, initrd. vmlinuz. as well as from menu.lst) from the boot folder, however my system manager still says that the folder is full.  

I'm running Hardy Heron 8.04. I'm really stuck, does anyone have any ideas? Thanks!

---

### Post by yeats on 2009-01-24
In a terminal window, you can do 

```
df -h
```

to see the amount of disk space taken up in each parition - that might be useful to post here.

You can also 

```
cd /boot
du -h
```

to see which files are taking up the most space, if that helps.

You can also do 

```
ls -l /boot
```

to see which files are the largest.

---

### Post by Kevbert on 2009-01-24
If the commands that chrissharp123 suggested that you use confirm that the boot Partition is full, please take a look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?p=6585114#post6585114")[/COLOR]. You've probably got a larger number of versions due to updates. When you use Synaptic it should remove the grub entries for you and free up some boot partition space.

---

