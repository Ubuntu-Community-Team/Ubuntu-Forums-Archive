---
title: "Beginner how to mount .iso to the desktop"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by powel212 on 2009-01-04
I know if I run

sudo mount filename.iso /media/isoimage/ -t iso9660 -o loop

I can mount a disc image to a folder, which is usually good enough, but is there another command line that will take a .iso image and make it appear as a mounted cd on the desktop?

Any help is appreciated.

Thanks

Powel

---

### Post by MenZa on 2009-01-04
It's probably possible with some hackeryjiggerypokery (yes, that's a technical term). Why would you need to do so? [imount[/i]'s iso9960 filetype with the loop option merely opens the contents of the iso file for viewing.

What are you trying to achieve?

---

### Post by powel212 on 2009-01-04
Trying to...

If i mounted the image and it appeared as a disk icon on my desktop it would just be a nice visual reminder that I had previously mounted the image. So I would then remember to unmount it when i was done. I have a tendency to work on several things at once and little visual reminders are helpful. Lest i forget, as i so often do. 

Powel

---

### Post by MenZa on 2009-01-04
I suppose you *could* just mount it into a folder on the desktop, like **sudo mount file.iso /home/yourusername/Desktop/isoimage -t iso9660 -o loop**, if that would be any better.

If you just leave it, what would be the issue with that? It's umounted when you shutdown your system, and not remounted when you boot it again.

---

### Post by powel212 on 2009-01-04
Good idea, and suggestion. I will give that a try.

Thank you

Powel

---

### Post by zvacet on 2009-01-04
@ **powel212**

If you want visual reminder you can use [gmountiso.]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html") It is graphic tool for mount/umount iso.

---

### Post by hashimoto on 2009-01-04
Try creating a mount point folder in /media and mount the iso there. That should bring up the icon on the desktop.

---

### Post by TheLions on 2009-01-04
or install CDEmu: [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

it can mount almost every CD/DVD image

---

### Post by Tim Sharitt on 2009-01-04
If you want the iso to show as a cd, mount it to /media/cdrom0. It should show up as a cd on you desktop.
```
sudo mount filename.iso /media/cdrom0 -o loop
```

---

### Post by powel212 on 2009-01-05
Thanks Tim

sudo mount filename.iso /media/cdrom0 -o loop

That is exactly what I was looking for.

I knew there had to be a way that easy. Awesome!

Powel

---

### Post by supererki on 2009-01-05
sudo apt-get install gmount-iso

Gmount-iso

---

