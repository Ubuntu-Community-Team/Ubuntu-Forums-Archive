---
title: "Graphics Software"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by lile001 on 2009-08-17
OK, I've got Gimp, and it is a great program if I want to really monkey-wrench a photo.  But frequently, all I want to do is take a batch of photos, and make scaled down copies of them.  This is possible in GIMP, but not really straightfor5ward, and you have to load each photo one by one.  50 photos?  Egads.  

At one time I had a package that would do something like this on Win-Doze, but it's been so long I can't even remember the name of it.  Is there a simple, straight forward package available under Linux that will batch convert graphics files?

---

### Post by Cheesemill on 2009-08-17
```
 
sudo apt-get install imagemagick
man convert

```

---

### Post by anaconda on 2009-08-17
after installin imagemagic
(sudo apt-get install imagemagic)
open a terminal and go to the directory which contains the images and type:

convert *.jpg -resize 50% pic.jpg

that would resize all pictures in the directory to be 50% of the orginal size. 
Convert newer destroys the original files, so you will have the original images and the new ones in the same directory..

Convert is a wery poverful program, with it you can eg. change pictures to a different format
eg. 
convert pic.jpg pic.png

or convert pictures to a .pdf document
convert *.jpg document.pdf

---

### Post by lile001 on 2009-08-17
Thanks!  It does everything I need, except it is a command-line interface.  All that typing!  Unless I want to convert everything in a directory, I'm still back to typing convert 100_1014.jpg -resize 25% 100_1014-s.jpg oops, failed - didn't capitalize something [gnashes teeth] convert 100_1014.JPG -resize 25% 100_1014-s.jpg (I type the wrong caps on at least one item in a long command-line entry at least every other time- brain not CAPS sensitive) 

It is probably possible to right click on a photo and have the computer just issue the above-mentioned command on it.  


> **anaconda said:**
> after installin imagemagic
(sudo apt-get install imagemagic)
open a terminal and go to the directory which contains the images and type:

convert *.jpg -resize 50% pic.jpg

that would resize all pictures in the directory to be 50% of the orginal size. 
Convert newer destroys the original files, so you will have the original images and the new ones in the same directory..

Convert is a wery poverful program, with it you can eg. change pictures to a different format
eg. 
convert pic.jpg pic.png

or convert pictures to a .pdf document
convert *.jpg document.pdf

---

### Post by Viva on 2009-08-17
Did you try [nautilus image converter]("apt:nautilus-image-converter")?

---

### Post by lile001 on 2009-08-17
> **Viva said:**
> Did you try [nautilus image converter]("apt:nautilus-image-converter")?


Excellent!  That really does the trick!  If i need anything more powerful, Image-Covnerter will work, but this  does 95% of my image manipulation in a click!

---

### Post by mcduck on 2009-08-17
> **anaconda said:**
> after installin imagemagic
(sudo apt-get install imagemagic)
open a terminal and go to the directory which contains the images and type:

convert *.jpg -resize 50% pic.jpg

that would resize all pictures in the directory to be 50% of the orginal size. 
Convert newer destroys the original files, so you will have the original images and the new ones in the same directory..

Convert is a wery poverful program, with it you can eg. change pictures to a different format
eg. 
convert pic.jpg pic.png

or convert pictures to a .pdf document
convert *.jpg document.pdf

actually your command would resize every image, but overwrite each image with the next one (since the output image name is the same all the time).

To resize all images you need a slightly more complex command:
```

for f in *.jpg; do convert $f -resize 50% resized-$f; done
```

Your command would work with mogrify, which simply overwrites the original image instead of creating a new one like convert does:
```
mogrify *.jpg -resize 50%
```

But I agree that Nautilus-image-converter is a great tool as well, and since it uses Imagemagick you now have both tools available. Imagemagick is excellent when you need to do complex manipulations for large quantities of images, since it can be easily scripted for very cool results which would take a lot of work with graphical image editors. For example I use Imagemagick to automatically create thumbnails that look like polaroid pictures, with image date written in bottom and each image slightly tilted in random angles, warped and with a drop shadow to create a realsitic effect of polaroid pictures scattered on the web page.

---

### Post by PatrickVogeli on 2009-08-17
Thanks! The nautilus extension is brilliant!! It works wonderfully, and it also works selecting various files, asking if overwriting or changing name.. nice!

---

### Post by ashwinhgtx on 2009-08-17
> **Viva said:**
> Did you try [nautilus image converter]("apt:nautilus-image-converter")?

Thanks a lot. Works perfectly. :P

---

### Post by anaconda on 2009-08-19
> **mcduck said:**
> actually your command would resize every image, but overwrite each image with the next one (since the output image name is the same all the time).

To resize all images you need a slightly more complex command:
```

for f in *.jpg; do convert $f -resize 50% resized-$f; done
```
[/CODE]


Sorry, but you are wrong. It does work. Try it if you don't believe. convert will create files with names: 
pic-0.jpg pic-1.jpg pic-2.jpg etc..

It is a very handy and smart program.....

But I have to agree that the nautilus extension is better option for the original poster.

---

