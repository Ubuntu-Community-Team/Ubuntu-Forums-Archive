---
title: "Disk Imaging/Cloning"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by dave66 on 2009-04-08
Hi,

Hoping somebody can help me. I want to get a number of people in the company I work for using Ubuntu on a Dell Mini-9. The Netbooks will essentially be in a pool so nobody will have "their own" unit, they will simply take one from the "pool stock" when they need one.

Ideally what I'd like to do is configure one of the Netbooks; my "plan" is that I'll setup one netbook out of the box, with location/language/time etc and so certain menu's will not be available (such as games), one application will run at start up, load whatever drivers are need for connected devices. Then create an image of that unit and put the image on an USB memory stick and then use the Memory stick to load the image onto the other Netbooks. Ideally I would like to take a new netbook out of the box and load the image without having to go through the normal first run setup.

Can anyone advice me of the best way to go about doing this or is it even possible? Bear in mind that I'm an Ubuntu newbie, but now that I have made the move from Windows to Ubuntu I want to encourage others to do the same ;)

---

### Post by HermanAB on 2009-04-08
Make a bootable USB stick then use netcat and dd to copy the disk image:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

---

### Post by kpkeerthi on 2009-04-08
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by dave66 on 2009-04-08
> **kpkeerthi said:**
> [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Thanks for that, it looks like exactly what I need and seems fairly straight forward for an Ubuntu newbie :D

---

### Post by dave66 on 2009-05-15
> **dave66 said:**
> Thanks for that, it looks like exactly what I need and seems fairly straight forward for an Ubuntu newbie :D

Just an update, for anyone trying to clone a Netbook or system running UNR it would seem that remastersys is not the solution.

I've been working with it for a couple of days not and no joy. I can create a backup ISO but it won't restore, so I posted to remastersys forum (great guys for a fast reply) and I'm told that it won't work:

[http://geekconnection.org/remastersys/forums/index.php?topic=138.0](http://geekconnection.org/remastersys/forums/index.php?topic=138.0)

So it's back to the drawing board :( which is a pity as the backup side of remastersys is really nice and easy to use. Guess I'll have to delve into using something like dd

---

### Post by unutbu on 2009-05-15
You might want to try Partimage instead of dd. Unlike dd, Partimage will only copy used portion of the partition.

The partimage package is part of the official repository.
See [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) for screenshots and documentation, and 
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522) for a tutorial.

---

### Post by dave66 on 2009-05-15
I have actually managed to clone a system. I resorted to creating a boot USB (DOS) and running Ghost.

---

### Post by NHArticleTen on 2009-05-15
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Sir Jasper on 2009-05-15
Hi,

You could google HDClone to see a reliable high quality paid solution. 

I expect you have given your proposal much thought. I hope so, else
what you want and what is needed may be far from identical.

I do know of an American doctor, who updated patient records daily 
on many laptops used by colleagues.

My regards

---

### Post by spcwingo on 2009-05-15
You might also want to check out ghost4linux.  More information here:

[http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

---

