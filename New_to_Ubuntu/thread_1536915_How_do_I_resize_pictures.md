---
title: "How do I resize pictures?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by papibe on 2010-07-22
I want to resize a set of pictures to a small mail/web size.

I haven't found a way to do it on F-Spot. And even though I have done some things with GIMP, it seems there's no a simple step to do this.

Right now, I think the only solution is to install a new image edit tool that includes the popular, important and valuable resize function.

Any suggestion?

---

### Post by sidzen on 2010-07-22
GIMP
Image => Rescale?

I keep the ratios locked and go down to 90 pixels X whatever
for avatars, other images.  Save as JPG about 90%, etc.
Something like this.

---

### Post by papibe on 2010-07-22
> **sidzen said:**
> GIMP
Image => Rescale?


There's no such option under the Image menu. At least in my version:
```
pablo@vaughan:~$ gimp --version
GNU Image Manipulation Program version 2.6.8

```

---

### Post by phillw on 2010-07-22
Hi, 

one image at a time?

[http://www.simplehelp.net/2007/08/13/how-to-resize-images-using-the-gimp/](http://www.simplehelp.net/2007/08/13/how-to-resize-images-using-the-gimp/)

or do you want to batch re-size?

If so, you will need [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php) which is so scary in what it can do it is untrue!!

A really good tutorial on just how good imagemagick can be found at [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)  the instructions are really good.

It is what I use to put the 'thumbnails' over on section two of [http://mgjuddltd.co.uk/index2.php](http://mgjuddltd.co.uk/index2.php)

e.g. [http://mgjuddltd.co.uk/auto_bulbs.php](http://mgjuddltd.co.uk/auto_bulbs.php) where the image is small, then expands when you click on the part.

I'm not sure if this what you are seeking, but it can be done.

Regards,

Phill.

---

### Post by papibe on 2010-07-22
Thanks a lot phillw!

So THERE IS one simple step option on GIMP (probably that was what sidzen was trying to tell me):

GIMP -> Image -> Scale Image...

@ phillw, I was "committed" to do the job one picture at a time.. but the ImageMagick was PRETTY helpful:

```
pablo@vaughan:~$ for file in *; do
> mogrify -resize 640x480 $file
> done

```

... and that was fast!.

Regards.

---

### Post by phillw on 2010-07-22
> **papibe said:**
> Thanks a lot phillw!

So THERE IS one simple step option on GIMP (probably that was what sidzen was trying to tell me):

GIMP -> Image -> Scale Image...

@ phillw, I was "committed" to do the job one picture at a time.. but the ImageMagick was PRETTY helpful:

```
pablo@vaughan:~$ for file in *; do
> mogrify -resize 640x480 $file
> done

```

... and that was fast!.

Regards.

The reason I not not post mogrify is that it so powerful and you do need to read about taking backups as if you mess up the command you loose everything. Just imagine trying it with 640x48 with no backup. It is akin to running commands with root privileges over your most important photographs.

<**_If you do not back up your important files, your files are not important_**>

It is, however, really easy to convert :D

Phill.

---

### Post by inzam on 2011-01-15
if  you want to resize image than i will you suggest you to visit the below link 
[http://www.raiseitsolutions.com/forum/viewtopic.php?f=4&t=3](http://www.raiseitsolutions.com/forum/viewtopic.php?f=4&t=3)
please visit the link, here you can know about how to resize image.
 thank you very much.

---

