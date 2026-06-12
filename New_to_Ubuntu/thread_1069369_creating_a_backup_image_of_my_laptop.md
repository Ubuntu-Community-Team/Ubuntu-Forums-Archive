---
title: "creating a backup image of my laptop"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by manuleka on 2009-02-13
i'm using an msi wind and i've been using Linux over it for over 3 months now... 

i want to change distribution --> toward Fedora, i don't want to dual boot so a fresh installation is my choice

can anyone tell me how to backup or create an image of my Ubuntu Drive so that if i want to roll back to ubuntu i can just install the image and everything will be back to it's current state... 

i have done alot of updates and installed alot of software packages so i don't want to go through the process of reinstalling everything... (days of re-installations)

---

### Post by kaibob on 2009-02-13
Have a look at:

Clonezillla
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Partimage
[http://www.partimage.org/](http://www.partimage.org/)

Ghost for Linux
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have personally used Clonezilla, and it works well, although grub issued error messages after a restore. I have used Acronis True Image for many years, and it also works well, but you have to pay for it.

---

### Post by llamabr on 2009-02-13
man mkisofs

but I wouldn't recommend this method.  It won't really take days to reinstall all those packages, and this image is going to be quite big.

---

### Post by manuleka on 2009-02-14
thanks guys... came across this:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

am going to work on it and post

---

