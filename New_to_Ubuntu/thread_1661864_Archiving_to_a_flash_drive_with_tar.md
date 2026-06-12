---
title: "Archiving to a flash drive with tar"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Windy_Chill on 2011-01-07
I am trying to archive some files to a flash drive using the tar command. I don't have any problems working within my normal file system.  When I try to place them on a flash drive the command seems to execute but, there is nothing on the drive. The flash drive is properly mounted and I am using the following command.

james@james-laptop:~/Pictures$ sudo tar cvf /dev/sdb Wallpaper .
Wallpaper/
Wallpaper/wallpaper_ubuntu.jpg
Wallpaper/img-wallpapers-3d-ubuntu-logo-g2shad-10575.jpg
./
./Wallpaper/
./Wallpaper/wallpaper_ubuntu.jpg
./Wallpaper/img-wallpapers-3d-ubuntu-logo-g2shad-10575.jpg

Can anyone tell me what I am doing wrong?

---

### Post by blind2314 on 2011-01-07
The syntax looks a bit off, try this.
 
```
tar cvf /dev/sdb/mystuff.tar *
```
 
Execute that from the directory that stuff currently resides in, i.e., your pictures directory.

---

### Post by seawolf167 on 2011-01-07
If you click the # when writing a message you can put it in code tags for better readability.

> **Windy_Chill said:**
> james@james-laptop:~/Pictures$ sudo tar cvf /dev/sdb Wallpaper

You want to add your file name/extension, specific a compression (j switch = .tar.bz2, z switch = .tar.gz, no z or j = .tar), tar defaults to folder recursion, so this should work:

```
tar jcvf /dev/sdb/my_wallpaper_backup.tar.bz2 Wallpaper/
```Folders/files are case sensitive, so Wallpaper is different from wallpaper

---

### Post by Windy_Chill on 2011-01-08
Thanks for the help. I tried the commands that you gave me and they worked perfectly within my normal file system.
```
james@james-laptop:~/Pictures/Wallpaper$ sudo tar cvf /test/wallpaper.tar *
img-wallpapers-3d-ubuntu-logo-g2shad-10575.jpg
wallpaper_ubuntu.jpg
james@james-laptop:~/Pictures/Wallpaper$ cd /
james@james-laptop:/$ cd test
james@james-laptop:/test$ ls
wallpaper.tar  
```However, when I try to place them on a flash drive mounted as /dev/sdb1 I get the following error.
```
james@james-laptop:~/Pictures/Wallpaper$ sudo tar cvf /dev/sdb1/wallpaper.tar *
tar: /dev/sdb1/wallpaper.tar: Cannot open: Not a directory
tar: Error is not recoverable: exiting now 
```I'm not sure what the problem is.

---

### Post by QLee on 2011-01-08
[QUOTE=Windy_Chill]...wallpaper.tar  [/CODE]However, when I try to place them on a flash drive mounted as /dev/sdb1 I get the following error.
```
james@james-laptop:~/Pictures/Wallpaper$ sudo tar cvf /dev/sdb1/wallpaper.tar *
tar: /dev/sdb1/wallpaper.tar: Cannot open: Not a directory
tar: Error is not recoverable: exiting now 
```I'm not sure what the problem is.[/QUOTE]

From the error dropped when you tried, I would say that the location you are trying to save to is not a directory.

Is there really a mount point in your filesystem "/dev/sdb1/" or is sdb1 mounted somewhere else? What is the result of running the command, mount, in a terminal window?

---

### Post by Windy_Chill on 2011-01-09
Yes, I got it to work! I guess you have to use the mount point in the file system. ie. /media/Volume/Wallpaper.tar and not the physical mount point ie /dev/sdb1.Wallpaper.tar. Kinda odd, because that's what the book that I'm reading says to do.  Anyway, it works! And thank you to everyone who responded to my posts.

---

