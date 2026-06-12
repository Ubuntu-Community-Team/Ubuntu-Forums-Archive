---
title: "Working with photos"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Scunnered on 2009-01-25
I am struggling with F-Spot as no matter what I try I can't resize despite their web site stating "***easily rotate, crop, resize***". I am attempting to convince my partner that Linux is exactly what she needs.

She currently uses Ifranview to resize pictures for downloading to the web and so far I am unable to replicate this feature in F-Spot despite their claims.  The user guide leaves a lot to be desired.

I am working purely with Linux and wish to keep everything that way.

Can anyone offer guidance on how I can resize pictures which will let me convince she who must be obeyed.

---

### Post by Stalker72 on 2009-01-25
Try **GIMP**.

```
sudo apt-get install gimp
```

Stalker72

---

### Post by Hallvor on 2009-01-25
Gimp might be an overkill, but it works.

Edit: Too slow.

---

### Post by gjoellee on 2009-01-25
If you are good at using GIMP you can make everything, but I must admit that Photoshop as better options and better UI.

---

### Post by chrisod on 2009-01-25
You could try Picasa.

---

### Post by llamabr on 2009-01-25
Gimp will certainly do the job, if you like hitting flies with sledge hammers.

Gimp is just a huge frontend for imagemagik anyway.  If you're comfortable with the command line, you can resize images easily with the resize command.  Here's some other simple commands for imagemagick:

[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)

hope they help.

---

### Post by cotcot on 2009-01-25
I am not sure. Maybe you have an older version. I have 0.4 on hardy and it also has not crop and resize possibilities in the edit. F-Spot latest version is 0.5.  I guess that the manual is about this version.
I do not work with f-spot. I use Digikam (0.9.3) and this allows cropping, red eyes, resize etc ... .

---

### Post by Scunnered on 2009-01-25
My thanks to you all.  Everything that I had read seemed to imply that Gimp was over kill. I was looking for something based on the KISS principals as that is my level.

Will have a look at your suggestions and see how I get along.

---

### Post by irfan9727 on 2009-01-25
Try mirage. Lightweight, and works!
*sudo apt-get install mirage*

---

### Post by clive littlewood on 2009-01-25
Hi

Mirage is both easy and powerful without all the "bells and whistles" of the Gimp.

It has Crop and resize options with preserve aspect option.

So all you need for internet resizing.     :D

Install through terminal       sudo apt-get install mirage

Clive

---

### Post by mikjp on 2009-01-25
gthumb

---

