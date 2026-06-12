---
title: "mounting issues in bash"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by coolmego on 2011-03-07
For mounting a hard-disk it is needed to create a folder in mnt directory...whenever i try to create a folder in mnt graphically it aint letting to do...can anyone say how to make a folder in shell...and how can i automise this mounting during the boot-time of the os...googling could not provide me with satisfactory answer...

---

### Post by Stephen Morgan on 2011-03-07
To create a folder in /mnt needs root priveleges, so you need to open the folder with a root nautilus. Either use
```
gksu nautilus
```
in the terminal, or just type
```
sudo mkdir /mnt/whateveryourhardrivewantstobecalled
```
To mount it automatically at startup you'll need to add a line to /etc/fstab, like this:
```
/dev/sda2 /slackroot ext4 errors=remount-ro 0 0
```
That's from my fstab, replace /dev/sda2 with the partition you want to mount, /slackroot with wherever you want to mount it (/mnt/whatever, for example) and replace ext4 if it isn't formatted as ext4.

You'll need to edit /etc/fstab as root, too, so 
```
sudo gedit /etc/fstab
```

---

### Post by coolmego on 2011-03-07
Thanks for your reply...but can i know what is "nautillus" and "fstab"...as i am trying to learn shell scripts..

---

### Post by HalfEmptyHero on 2011-03-07
The reason you can't create the folder using nautilus is because you need root privileges to do so. You can either hit alt + F2 and type in gksudo nautilus or fire up the terminal and type in sudo mkdir /mnt/folder_name with folder_name being whatever you want. I recommend not putting any spaces in the folder name, but if you do, you need to put a slash in front of it. So if you wanted it to be named External Files, you would type in sudo mkdir /mount/External\ Files.

As for automount, you can achieve this by editing your fstab. [Here]("http://ubuntuforums.org/showthread.php?t=283131") is a tutorial on how to do that.

Edit: I was too slow I guess. Nautilus is the file manager. When you open a folder, you are using nautilus, it is not a shell script. Go to the tutorial I posted, it will tell you all about fstab.

---

