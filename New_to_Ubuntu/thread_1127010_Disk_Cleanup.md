---
title: "Disk Cleanup"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by RealG187 on 2009-04-16
Okay I am running out of space on my Laptop's hard drive and I have Ubuntu installed. Are there any unnecessary files Ubuntu makes I can delete (or a program that deletes them like cleanmgr.exe for Windows)?

I think there is a thumbnail folder in ~/.something (when I backup this drive I notice changes made to it since the last backup). Can I delete that?

Anything else that I can delete that I don't need that grabs up space.

What about using a package manager and deleting packages for programs I no longer use?

---

### Post by adobrakic on 2009-04-16
Not sure for the specific folder, but for cleaning stuff up I do:

```
sudo apt-get autoremove --yes; sudo apt-get clean --yes;
```

---

### Post by balaknair on 2009-04-16
You can safely delete the thumbnails folder(nautilus will gradually build it up again though unless you disable thumbnail previews via edit>preferences in nautilus).
Delete the Trash bin contents to regain some more space.

Try using Disk usage analyzer to find what files/folders are taking up space
(Applications> Accessories> Disk usage analyzer)


***sudo apt-get autoremove*** will remove unneeded packages and config files, and ***sudo apt-get autoclean*** will remove incompletely installed packages, ***sudo apt-get clean*** will clear the apt-get cache. These three can reclaim quite a bit of space for you depending on how old the install is and how many packages you have installed.
Uninstalling kernel versions other than the one you're using can free up around 200-300 MB for each version. Do this only if you're sure you know what you're doing. 

You can also regain space by uninstalling localisation files you don't need. Use a script named localepurge for this
[B][I]sudo apt-get install localepurge
sudo localepurge[/I][/B]

You get a list of locales installed on your system, choose the one(s) you want to keep and the rest will be deleted.

---

### Post by kpkeerthi on 2009-04-16
> **RealG187 said:**
> Okay I am running out of space on my Laptop's hard drive and I have Ubuntu installed. Are there any unnecessary files Ubuntu makes I can delete (or a program that deletes them like cleanmgr.exe for Windows)?

I think there is a thumbnail folder in ~/.something (when I backup this drive I notice changes made to it since the last backup). Can I delete that?

Anything else that I can delete that I don't need that grabs up space.

What about using a package manager and deleting packages for programs I no longer use?


1. Yes. It is safe to remove ~/.thumbnails folder. [http://ubuntu.wordpress.com/2006/02/15/clean-up-old-thumbnails/](http://ubuntu.wordpress.com/2006/02/15/clean-up-old-thumbnails/)

2. Clean up junk: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

3. Remove unused kernels: [http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3)

---

### Post by RealG187 on 2009-04-16
I never installed any kernels, so do I only have one (unless Ubuntu comes with more than one...)?

---

### Post by balaknair on 2009-04-16
Kernels: Ubuntu comes with just one, but as you update the system, when the kernel is updated, previous versions of the kernel are retained(as a backup or safety option should the new version cause problems on your hardware).
eg: Ubuntu 8.10 shipped with Kernel 2.6.27-7, which was then updated to 2.6.27-9 and then to 2.6.27-11
So at this point, you'd have three versions of the kernel(on boot-up, you'd normally see the choices in your GRUB menu for each kernel version).

---

### Post by kpkeerthi on 2009-04-16
> **RealG187 said:**
> I never installed any kernels, so do I only have one (unless Ubuntu comes with more than one...)?

If have you been updating Ubuntu since you installed it, chances are you have more than one kernel. You can check that in your GRUB menu and Synaptic (Search for **linux-image** and sort on the first column to see all installed packages marked in green)

---

### Post by Paqman on 2009-04-16
You can remove old kernels in Synaptic, btw. Search for linux-image to find them. Make sure you don't remove your current kernel though. You can check which kernel you're currently using with the command:
```

uname -r

```

---

### Post by RealG187 on 2009-04-16
I still have -7. I don't update, the next time I update would be if I reinstall (I wanna save bandwidth).

Plus I hear if you update your kernel VMWare no longer works.

---

### Post by Sonsum on 2009-04-16
I have an old laptop which I have ubuntu installed. As you can imagine, dual booting ubuntu + windows 2000 can be pretty tough for a 4 gb hard drive.

I usually don't have enough space for a ubuntu update, so I use apt-get autoremove; it usually frees up at least 700 mb.

I used this guide (lots of great tips): [http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by RealG187 on 2009-04-20
While updating my backup I reviewed the list of changed folders and listed some which I think are safe to delete, can I delete them?

~/.compiz/session
~/.evolution/cache/tmp (there is a file or files containing "mail.log" in their name)
~/.gftp/cache
~/.java/deployment/cache/6.0/37 (or just the whole cache folder or the files in this folder)
~/.java/deployment/cache/6.0/host (see above)
~/.macromedia/Flash_Player/#SharedObjects/#### (there is a folder with some numbers, not sure if it has the same name on every system or it's different)
~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
~/.opera/cache4
~/.opera/opcache
~/.opera/images
~/.purple/logs/yahoo/account (or just the whole logs folder or the files in this folder))
~/.thumbnails/fail/gnome-thumbnail-factory (or just the whole .thumbnails folder or the files in this folder)
~/.thumbnails/normal (same as above)
~/.wine/dosdevices/c:/windows/temp (*)
~/.wine/drive_c/windows/temp (*)

* Those two .wine folder for drive C:\ are symlinked so they are the same. just delete the contents of the temp folder.

---

### Post by anystupidname on 2009-04-20
Might I suggest one of the following:
baobab
kdirstat
filelight
fslint
du -k / | sort -n
df -h

---

### Post by juancarlospaco on 2009-04-20
**Bleachbit**
*I have been writed some cleaners on this proyect*

---

