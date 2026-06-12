---
title: "batch pic resizeing app??"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by mishkin on 2009-02-18
What should i use to batch resize my pics from a 6mbit camera to about 25% of origonal pics

can be cli or gui...

simple is a added bonous and I'd like it to not lower the quality of the pics (keep it 100%) 

thx

---

### Post by Rolcol on 2009-02-18
I don't have experience with it but you can use the imagemagick suite to batch resize.  Imagemagick is in the repositories as "imagemagick" (no typo.  It's supposed to have a "K").  Imagemagick is command-line, however.

```
sudo apt-get install imagemagick
```

Help:  [http://www.imagemagick.org/script/command-line-processing.php](http://www.imagemagick.org/script/command-line-processing.php)

---

### Post by fooman on 2009-02-18
there is a plugin for nautilus that will resize images from the right-click context menu...i am pretty sure it works with multible/batch images.  in a terminal:

```
sudo apt-get install nautilus-image-converter
```then just right click on the pics and look for "resize images" in the menu.

enjoy.

---

### Post by mcduck on 2009-02-18
nautilus-image-converter is nice, but using tools from Imagemagick give you better control over what's going on (and actually allow you to do a lot more than simple resizing)..

To resize a directory full of .jpg images to 25 % with 100% quality you would use something like this:
```

for pic in *.jpg; do convert "$pic" -resize 25% -quality 100 small-"$pic"; done
```
(this will save the resized images with "small-" added to beginning of the file name.)

The best way to use Imagemagick is of course to write your image manipulation tasks into scripts, so that you don't need to run complex commands all the time but simply open a terminal where you have your images and then start your script to process them all. For example you could easily make a small script that resizes all your images to couple of different sizes and renames them based on EXIF data.. Or creates a web gallery from your photos and uploads it to your server with FTP.. ;)

---

### Post by mishkin on 2009-02-28
I'll try nautilus-image-converter for now

thats what I had on my windows desktop a right click feature, was quite handy


edit: it installed but I have no resize on the menu when right clicking a jpg...

---

### Post by mishkin on 2009-03-04
the gimick program was already installed and the resize in right click has now appeared after a restart

---

