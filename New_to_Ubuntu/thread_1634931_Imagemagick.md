---
title: "Imagemagick"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by newkid2010 on 2010-12-01
Hi guys,

I'm totally new to ubuntu and i'm trying to convert several .png images to .pgm using imagemagick. I have imagemagick installed but it wont read the images i.e. do i have to move the wanted pictures to a particular folder assosciated with image magick, if so what folder is this?

thanks for any help

---

### Post by lykeion on 2010-12-01
Hi and welcome to Ubuntu.

ImageMagick is a library to display, convert, edit images. 
It consists of several command-line commands and the one you are looking for is convert.

1. Start a terminal (Applications > Accessories > Terminal)
2. Navigate to where your images are (change path to your actual path)```
cd path/to/images
```
3. Use ImageMagick convert command to convert from PNG to PGM```
convert image.png image.pgm
```
If you have many PNG images you can use a for-loop like this
```
for i in $(ls *.png); do convert "$i" $(basename $i .png).pgm; done
```

---

### Post by newkid2010 on 2010-12-01
thanks very much works perfectly :)

---

