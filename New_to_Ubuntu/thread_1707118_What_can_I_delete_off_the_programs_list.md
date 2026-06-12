---
title: "What can I delete off the programs list?"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by icutler on 2011-03-14
Hi, I was just wanting to know what items I can safely delete off the programs list on Ubuntu 10.10 (including technical items).

---

### Post by 5149.5 on 2011-03-14
The first thing I cleaned out were all of the games. Just bring up the software center and read the descriptions of the apps. If it sounds like something you'll never use, un-install it. Some of them will give you a warning about removal. Go kind of slow and see what you use.

---

### Post by I2k4 on 2011-03-15
It's personal of course.  On versions I've tested I've gotten rid of all "Internet" tools except the browser and installed DropBox.

I got rid of photo/image editors and installed GIMP.  Using Google Docs and need OpenOffice so removed it.  Use online email so removed local.  

My caution would be to not try to remove too many at once.  One or two applications at a time, to prevent the package manager from tripping over itself.  Same caution for installing new packages.

---

### Post by IHeequ5i on 2011-03-15
+1 for deleting one or two things at a time. I got myself in a snarl trying to delete 4 packages at once.

---

### Post by xptional on 2011-03-15
you can check the program list by typing ```
 dpkg -l | more 
``` and then see what you want to delete, for deletion please use this one ```
sudo apt-get remove *packagename*
```  or  ```
 sudo apt-get autoremove packagename

```

hope it helps you :)

---

### Post by Kirboosy on 2011-03-15
Its all personal preference. Just don't get click happy in Synaptic Package Manager and watch what you remove. If it wants to remove parts of Ubuntu-desktop then chances are you won't want to remove the package. 

I know that one of the Evolution packages can't be removed because it will take Gnome and ubuntu-desktop with it...

---

### Post by uRock on 2011-03-15
Just remember to look at the dependency packages that will be uninstalled with the programs. If it shows ubuntu-desktop anywhere in the packages to be removed, then you'll want to cancel the removal.

---

### Post by I2k4 on 2011-03-15
Re removing "Desktop", it came up in removing mtPaint from Lubuntu, for GIMP.  It stopped me for a while, but eventually I did remove it, without any harm.  I still don't know what it is, since nothing changed.  (Advantage of testing on Live USB, no serious fear of being wrong.)

---

