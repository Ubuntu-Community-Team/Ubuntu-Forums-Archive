---
title: "Photo size reduction"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by arno48 on 2011-06-28
I have to send a 1250 Kb photo to a site who does not accept photo heavier than 250 Kb.
Could you please suggest me an application able to reduce photo size and suitable to my Natty.
Thanks

---

### Post by aeiah on 2011-06-28
you could use an image editor like gimp, or probably whatever is in your images menu that looks like it could do it. or you could do it on the command line with imagemagick:
```

convert filename.jpg -resize 50% newname.jpg
```

this won't necessarily get it below 250k of course, but its probably easierto do it this way with trial and error

---

### Post by Rex Bouwense on 2011-06-28
Just right click on the photo and choose resize.  All the options are there.

---

### Post by dFlyer on 2011-06-28
Nautilus-image-converter will resize you photos with the click of a mouse in Nautilus.

From a terminal enter:

sudo apt-get update && sudo apt-get install nautilus-image-converter

Open nautilus and under edit select Resize image. It's that easy.

---

### Post by arno48 on 2011-06-28
> **dFlyer said:**
> Nautilus-image-converter will resize you photos with the click of a mouse in Nautilus.

From a terminal enter:

sudo apt-get update && sudo apt-get install nautilus-image-converter

Open nautilus and under edit select Resize image. It's that easy.


Awfully embarrassing.
I installed nautilus-image-converter, and in fact in Ubuntu Software Center I read
"nautilus-image-converter (0.3.0- 3ubuntu2) installed at 18.25

but I am not able to open this application.
I typed it in Launcher but without results.

---

### Post by chmac on 2011-06-28
You need to restart your session, then you can right click on an image and you'll see the resize menu in nautilus (the file manager). That's what nautilus-image-converter does. It's not an application you can run directly, you access it within the context (right click) menu in Nautilus.

---

### Post by mike555 on 2011-06-29
You might also want to remove the images metadata , there is a command line app called "jhead" that can remove all metadata from images in a folder by typing " jhead -purejpg * " in terminal, in that folder ..

it helps to have installed " nautilus-open-terminal ", so you can just right click inside the folder and it will open terminal inside that folder, so you don't need to cd to it.....

---

### Post by amjjawad on 2011-06-29
**nautilus-image-converter** is the package name that you need to install either from Synaptic or from terminal and it's NOT installed by default, you need to install it, **LOG OFF** then login again and it should work.

---

### Post by arno48 on 2011-06-30
> **chmac said:**
> You need to restart your session, then you can right click on an image and you'll see the resize menu in nautilus (the file manager). That's what nautilus-image-converter does. It's not an application you can run directly, you access it within the context (right click) menu in Nautilus.

It's a very useful tool, thanks for your clever and friendly explanation.

---

### Post by mike555 on 2011-06-30
Another thing that works well is the "RIOT" plugin for Gimp .......it comes with the Gimp-Plugin-Registry ,from the package manager.

---

### Post by beew on 2011-06-30
[http://www.shrinkpictures.com/](http://www.shrinkpictures.com/)

---

### Post by SoFl W on 2011-06-30
> **mike555 said:**
> You might also want to remove the images metadata , there is a command line app called "jhead" that can remove all metadata from images in a folder by typing " jhead -purejpg * " in terminal, in that folder .

Thank you, I knew something like this existed in Linux, but wasn't sure where.  I just hoped GIMP got rid of all unnecessary garbage.   I had an OLD DOS/Win95 program that would remove all the extra garbage, it was called jpgcleaner, was hoping for something like what you mentioned.

Edit:
It reduced the file sizes of the files I created with GIMP, so that is good.

---

### Post by jtarin on 2011-06-30
I've always used Gimp for this......way before Nautilus.......but way after [ImageMajick]("http://www.imagemagick.org/Usage/")

---

