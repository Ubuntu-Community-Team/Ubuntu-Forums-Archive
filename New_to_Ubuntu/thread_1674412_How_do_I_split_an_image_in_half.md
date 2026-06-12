---
title: "How do I split an image in half?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Odexios on 2011-01-23
I have a lot of pictures (around ten thousand) I need to split in half.

I obviously can't do that manually, so I tried to look for some command-line application, and I though that econvert could help me; but I couldn't figure out from the manpage how to correctly use the option --split, so I'm back at the start point.

Can anyone help me?

---

### Post by rezaervani on 2011-01-23
You can use split command

> split -b (outputsize) (inputfile0for example :

> split -b 300m bigfile.odtwill split your file into some files with 300MB size.

to recover use cat command :

> cat file1 file2 file3 > bigfile.odt

---

### Post by Odexios on 2011-01-24
I'm sorry, I think I haven't been clear [img]http://forum.gamesvillage.it/images/smilies/asd.gif[/img]

I mean I have to split the picture in two parts, graphically, and get one picture with the left half and one with the right one.

---

### Post by vanadium on 2011-01-24
Using "convert", you could, in one pass, crop the images to retain only one half, and in a second pass, crop the images to retain only the bottom half. I am not sure there will be a direct option to split the image in two parts.

---

