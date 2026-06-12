---
title: "images converter"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by hemoali on 2011-03-09
I want a program to reduce images size to less than half to put it in site because the images make the page loading is very slow
or any image converter

---

### Post by wizard10000 on 2011-03-09
The easiest way to do it is to install imagemagick -

```
sudo apt-get install imagemagick
```

then use mogrify to resize the images.

```
mogrify -resize 50% *.jpg
```

But - you can also change the quality of the image to make the file size smaller and that might help as well; maybe the right solution is a combination of both - you can find all of mogrify's options here and it's a little easier to read than the man page -

[http://www.imagemagick.org/www/mogrify.html](http://www.imagemagick.org/www/mogrify.html)

Hope this helps -

---

### Post by treesurf on 2011-03-09
Or if you want something even simpler do

```
sudo apt-get install nautilus-image-converter
```

Then you can right click on a picture, or group of pictures, and it will give you options to resize or rotate with various possible settings.  Very nice and easy.

---

### Post by wizard10000 on 2011-03-09
> **treesurf said:**
> Or if you want something even simpler do

```
sudo apt-get install nautilus-image-converter
```


That's what I get for running KDE  :D

---

### Post by hemoali on 2011-03-09
but how can i use it it is not a program

---

### Post by col48 on 2011-03-09
mogrify is a program you would run in a Terminal.

ie Applications>Accessories>Terminal
then in the terminal
```
cd folder-where-the-images-are
mogrify -resize 50% *.jpg

```

This assumes the images are jpg, that there are no other jpg files in the folder and that you do not want to retain the unmodified versions of the images.

Nautilus-image-converter would add functionality to Nautilus (the file browser), so it is a subprogram rather than an independent program.

The apt-get stuff is to install the packages which make the (sub)program available for use.

(I've never used either, but this is my reading of these posts).

---

### Post by mastablasta on 2011-03-09
> **wizard10000 said:**
> That's what I get for running KDE :D
 
well try to find same thing for Dolphin in the Kpackagekit :-P
 
 
Otherwise you can always use gimp for Pic by Pic resize. I forgot how the default pic viewer in Kubuntu is called. i think gweber or something like that. anyway i am sure it also has pic resize option.
 
It owuld be strange to me that this option wouldn't exist in Linux (multiple resize) as it does in windows viewers since way back from the 90's.

---

### Post by wizard10000 on 2011-03-09
> **mastablasta said:**
> well try to find same thing for Dolphin in the Kpackagekit :-P

I'm allergic to kpackagekit  :P

I've tried hard to like muon and it ain't bad, but I still keep falling back to synaptic.

---

