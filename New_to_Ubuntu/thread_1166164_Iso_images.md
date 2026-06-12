---
title: "Iso images?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by cobaltseeker on 2009-05-21
So, How do CD image files work on Linux? I have a ton of CD Images that i've been able to mount (that's step one) but i also need to CREATE some iso images off of CDs... i think.

Duh,  to resay that - i have a CD i want to have always mounted (iso file would be how i'd do that in windows...) how can i get it mounted? Do i need to also create an iso on linux? (i don't have one yet, so i have to make it now and i'm trying to NOT boot into windows to do it :P) or is there some other way to mount a CD's contents?

many thanks :)

(btw, if i do have to create an iso - any tips on a certain prog i can use? i found isomaster but all that does is read/extract iso files)

---

### Post by cobaltseeker on 2009-05-21
Ooh i may have figured it out (i thought i tried this earlier... apparently not)

my solution ( i think, will edit if this work(ed) ) is to navigate to the CD and just 'burn' the cd to an image - it's not ISO but it's something else? Let's see if it mounts... 

and whats "brasero" ? O.o

---

### Post by Bucky Ball on 2009-05-21
[http://www.electrictoolbox.com/howto-mount-iso-image-linux/](http://www.electrictoolbox.com/howto-mount-iso-image-linux/)

---

### Post by Cheesemill on 2009-05-21
You can create an .iso image from a CD using the terminal with the following command:
```
dd if=/dev/cdrom of=image.iso
```

If you want to create an image from existing files you can use ISO Master (it's in Add/Remove Programs).

Cheesemill

---

### Post by TpyKv on 2009-05-21
that is correct, you can just click on the iso image and ubuntu will open brasero, the disc/iso burning program and it will take care of the rest!

it can also make a .toc extension, I always let ubuntu choose the safest option unless you are working with windows files in which case iso always works best...

---

### Post by superprash2003 on 2009-05-21
[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

---

### Post by cobaltseeker on 2009-05-21
you people rock :) 

what i tried didn't do what i wanted, will look through your links!

---

### Post by cobaltseeker on 2009-05-21
> **Cheesemill said:**
> You can create an .iso image from a CD using the terminal with the following command:
```
dd if=/dev/cdrom of=image.iso
```If you want to create an image from existing files you can use ISO Master (it's in Add/Remove Programs).

Cheesemill


Okay what i was looking for was how to CREATE the iso - i figured out how to mount them..

trying this out - gosh i'm obsessed with ubuntu O.o

---

### Post by Bucky Ball on 2009-05-21
Brasero is the go for burning an ISO!

Hey, that rhymes! 'Burn Image' and you have it. Select the image to burn and you're there. :)

---

