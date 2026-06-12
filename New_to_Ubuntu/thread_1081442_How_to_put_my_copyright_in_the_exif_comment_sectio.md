---
title: "How to put my copyright in the exif comment section of an image?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by kramer65 on 2009-02-26
Hi,

Since a little while I am photographing some little events. Since I do want credit for my work I want to put my name in the comment section that you see when you do a right click > properties.

I thought of using Gthumb. So I changed the comment (edit > comment), but that only seems to work inside of Gthumb. When I do in nautilus rightclick > properties > comments, I still see nothing.

Does anybody know how I can do this?

---

### Post by Ripose on 2009-02-27
In Nautilus it is Right Click --> Properties --> Notes

However if you want to embed your signature so it cannot easily be removed use GIMP

---

### Post by Kellemora on 2009-02-27
Hi Kramer

Using the center grid in the Rule of Thirds, locate a fairly solid object and embed your copyright notice there.  This way it cannot be cropped out, although it could be cloned out if someone knew it was there to find it.

So it don't show, you want to embed the text within the resolution it will be reduced to, but placed while you have the image at a very high resolution.  Select a shade only 1 or 2 steps lighter than the existing image.  I often use easy to find locations, such as a watch band, purse strap, eyeglasses ear piece on portraits.  On scenes I look for a consistent area near the center of the image.

As an example If you blow up an image like a 5x7 to 22x34 and use 2 point type 2 shades lighter, at 5x7 it will be completely unnoticeable.  If blown up to 9x12 it might be seen but not read and won't appear when printed.  If you try going as large as 44x68 on a 5x7 reduction, it will become unreadable, so you have to know what your final resolution is going to be for the final image as distributed.

FWIW:  The laws are different now too!  If you have the original, even in digital form, that original IS your proof of copyright.  Just make sure you NEVER distribute it at the original resolution or your SOL.

TTUL
Gary

---

### Post by kramer65 on 2009-03-02
Hi Kellemora,

Thanks or the elaborate answer. This is great for distributing small amounts of pictures. The problem is that it was a little job for a student organisation. I don't get a lot of money for it and the pictures weren't very special (how good can pictures be of drunk partying people?), but most importantly it were a lot of pictures (about 300).

For this reason I just wanted to put my name in the comments sections so that it can't be seen on the picture itself. I know people can even delete the comment easily, but I just hope to get some credit for the pictures so that I get jobs in the future..

I will for sure use your tips for future jobs, but do you have any tips on how I can add my copyright notice to the comments sections of a large amount of images? So some kind of batch command..

---

### Post by Kellemora on 2009-03-02
Hi Kramer

Because each program that can open an image uses a different type of text system or info page, I never bother with using them.

BUT, you can make a new IMAGE SPACE 1/4 inch taller or more if necessary than the original image and past the image to the new Space.
Or add white space at the bottom of an image.
And use this area for you Text, notations and copyright info.

When printed they can easily crop out the bottom, but leave the original intact.

I use something like this for family group photo's, so I can put each persons name on the border of the image in plain legible text.

For heavily populated group photos, I use an OUTLINING program (sometimes called coloring book outline) and place a number within each image, then that is included as part of the original picture, usually below it on the page and of course, cropped down so you only have the necessary part of the image with numbers.

Regardless of how I do what, I ALWAYS make the added part integral with the image itself so it can be read and viewed using any image viewer.

I wasted a lot of years using program specific tools only to find when that program was no longer available, there was NOTHING out there that could access all that extra work I went through.  So now, everything becomes a part of the image itself.  But I still maintain the original size of the image too.  Meaning if it was a 5x7 image, the image itself is still 5x7, but the background it rides on is now 5x11 so the coloring book image uses a 5x4 area below the image.

Hope that made sense!

TTUL
Gary

---

### Post by yther on 2009-03-02
If I understand you, you want to set (automatically, many files in one operation) your own comment field on a bunch of images, right?  Try installing **jhead** (it's in the repositories) and I believe you'll find it useful.  From "man jhead":

> **-ce**

Edit the JPEG header comment field (note, this comment field is outside the Exif structure and can be part of Exif and non Exif style JPEG images).
A temporary file containing the comment is created and a text editor is launched to edit the file. The editor is specified in the EDITOR environment variable. if none is specified notpead or vi are used under Windows and Unix respectively. After the editor exits, the data is transferred back into the image, and the temporary file deleted.
**-cs** file
    Save comment section to a file 
[COLOR="Lime"]**-ci** file
    Replace comment with text from file [/COLOR]
**-cl** string
    Replace comment with specified string from command line file 

Note that I haven't used it (but I might one day), however it seems to fit the bill.  :)

---

### Post by stani on 2009-06-27
> **kramer65 said:**
> Hi,

Since a little while I am photographing some little events. Since I do want credit for my work I want to put my name in the comment section that you see when you do a right click > properties.

I thought of using Gthumb. So I changed the comment (edit > comment), but that only seems to work inside of Gthumb. When I do in nautilus rightclick > properties > comments, I still see nothing.

Does anybody know how I can do this?

Use Phatch which has a nice GUI for it:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

---

### Post by niteshifter on 2009-06-27
Hi,

The package exiv2 will do that and supports batch changes. Do read the man page first. Or you could roll your own - basically to change the Copyright field (for the file image.jpg):
```
exiv2 -M"set Exif.Image.Copyright YourNameHere" image.jpg
```
The above could be used in a simple shrell script / for loop. Or in an exiv2 cmd file (for batching).

I know you said "comment section" - but that's a bit problematic: EXIF has a couple of comment fields (tags), which one? There is, however only one tag in the EXIF standard for copyright info.

---

### Post by stani on 2009-06-27
> **niteshifter said:**
> Hi,

The package exiv2 will do that and supports batch changes. Do read the man page first. Or you could roll your own - basically to change the Copyright field (for the file image.jpg):
```
exiv2 -M"set Exif.Image.Copyright YourNameHere" image.jpg
```
The above could be used in a simple shrell script / for loop. Or in an exiv2 cmd file (for batching).

I know you said "comment section" - but that's a bit problematic: EXIF has a couple of comment fields (tags), which one? There is, however only one tag in the EXIF standard for copyright info.
Phatch uses exiv2 for the backend and wraps it in a nice graphical user interface.

---

### Post by John Comeau on 2011-03-13
> **kramer65 said:**
> Hi,

Since a little while I am photographing some little events. Since I do want credit for my work I want to put my name in the comment section that you see when you do a right click > properties.

Does anybody know how I can do this?

realize this is an old thread, and there are already several ways to do this posted, but here is one more, from the Debian exif package:

```
exif --ifd=0 --tag=Copyright  --set-value="Copyright 2011 John A. Photographer, all rights reserved" -o ~/blog/photo.jpg ~/blog/photo.jpg
```

If the photo has no exif data to start with, you need to first create it:

```
exif -c -m -o ~/blog/photo.jpg ~/blog/photo.jpg
```

---

