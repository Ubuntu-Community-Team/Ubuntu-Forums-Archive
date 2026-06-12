---
title: "Batch image processing"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-10
Hi,

My enquiry; is there an application that can do this? I couldn't find within GIMP, and irfanview isn't built for Linux :( Although I did try to work it, but got stuck after the install. 

Thanks!

---

### Post by hungryOrb on 2009-04-10
Oh my.. tried to make install for imagemagick, but apparently I don't have a compiler, so I went for the easier option of a .deb.
Not so easy, trips up on downloading the files, complaining that I gotta check my net connection.
Anyone know a surefire way to get batch image processing? :'(

TFC

---

### Post by hungryOrb on 2009-04-10
This is happening at every turn:

```
W: Failed to fetch http://mirror.rootguide.org/ubuntu/pool/main/g/gcc-4.2/libgfortran2_4.2.4-1ubuntu3_i386.deb
  Could not connect to mirror.rootguide.org:80 (221.133.227.247). - connect (111 Connection refused)
```

Could it be connected to my location in Shanghai?
Eep.
Robin

---

### Post by hungryOrb on 2009-04-10
Here's another:

```
gen@gen:~$ sudo apt-get install imagemagick --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  imagemagick
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1421kB of archives.
After this operation, 4571kB of additional disk space will be used.
Err http://mirror.rootguide.org hardy/main imagemagick 7:6.3.7.9.dfsg1-2ubuntu1
  Could not connect to mirror.rootguide.org:80 (221.133.227.247). - connect (111 Connection refused)
Failed to fetch http://mirror.rootguide.org/ubuntu/pool/main/i/imagemagick/imagemagick_6.3.7.9.dfsg1-2ubuntu1_i386.deb  Could not connect to mirror.rootguide.org:80 (221.133.227.247). - connect (111 Connection refused)
gen@gen:~$ 

```

:P

Cry :(

---

### Post by kaibob on 2009-04-10
> **hungryOrb said:**
> Oh my.. tried to make install for imagemagick, but apparently I don't have a compiler, so I went for the easier option of a .deb.
Not so easy, trips up on downloading the files, complaining that I gotta check my net connection.
Anyone know a surefire way to get batch image processing? :'(

TFC

You do not need a compiler; you can install Imagemagick with Synaptic. If Synaptic is having trouble downloading, change to a different repository (under the "Setting" menu).

Batch processing can also be done with Phatch:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by computermacgyver on 2009-04-10
As Kaibob wrote, trying changing your "Software Source"

System->Administration->Software Sources
change the drop-down under "Download From"

There are also some plugins for gimp to do batch resizing, search online.

And please look at this thread for many more options:
[http://ubuntuforums.org/showthread.php?t=170862](http://ubuntuforums.org/showthread.php?t=170862)

---

### Post by hungryOrb on 2009-04-10
WOW! I cannot put into words my exact appreciation! but THANKYOU!

2 options are enough for me!

Peace!
Robin

---

