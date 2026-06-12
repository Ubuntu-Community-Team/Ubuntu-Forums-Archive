---
title: "Installing software from ISO Image"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by vikas barnes on 2010-07-28
Hi :p,
 I use **APTONCD** software to create software cds to install on my home system because I don't have Internet connection. I prepare the CD at my Office PC and than use it on my computer. 
Can u guys tell me the way, that without burning a CD I can use **ISO** image of APT CD to install the software. Also i m getting error in installation of** ttf-ms-core-font-installer** available in **ubuntu restricted extras package** this way, because of this the some fonts r not installed on my computer.

---

### Post by SkyNet2029 on 2010-07-28
Hi.
While you could use the kernel loop mount function, this might work out better for you.
 
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
 
Hope that helps

---

### Post by Deiz on 2010-07-28
You can do a loopback mount via:

```
sudo mount -o loop -t iso9660 YOURISO /media/cdrom/
```

---

### Post by vikas barnes on 2010-07-28
Thanks for your sugessions, I seems working.

---

### Post by mcduck on 2010-07-28
If you are running Ubuntu 10.04 you can simply right-click any .iso image and select "Open with Archive Mounter". That will mount the image for you... ;)

What comes to the MS fonts installer package, the problem is that some of the fonts aren't allowed to be distributed in the package. When you install the package it actually tries to download those fonts for you. Of course that won't work if you don't have Internet connection. The solution is to simply find a computer with Windows installed and copy the fonts from there manually.

There are some packages like this in the repositories, for things with such a restrictive licensing that they can't be distributed directly from Ubuntu's servers.

---

