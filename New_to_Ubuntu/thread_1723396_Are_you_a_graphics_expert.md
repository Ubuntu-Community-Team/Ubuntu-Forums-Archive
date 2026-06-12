---
title: "Are you a graphics expert?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by suomalainen on 2011-04-07
Ubunteros,

I suffer from the grainy .gif syndrome. Every time I try to post a gif image on the web (web site, photo bucket) it is grainy and just doesn't look right.

I finally found a resource that states how to fix the issue, see:

[http://www.infocellar.com/graphics/grainy-gif-fix.htm](http://www.infocellar.com/graphics/grainy-gif-fix.htm)

But this is a windows program!!! 

Would anyone have a suggestion as to how to go about this using Linux Ubuntu programs already available?

Thank you very much!

---

### Post by wep940 on 2011-04-07
I haven't really ever checked, but perhaps GIMP either has a built-in or there is an add-in to do that.

---

### Post by Zimmer on 2011-04-07
Not got time to read it all now
[http://docs.gimp.org/en/gimp-image-convert-indexed.html](http://docs.gimp.org/en/gimp-image-convert-indexed.html)

Having read the link you gave it appears they are creating a custom palette from the image in order to 'smooth' the gif.

Steps to take with GIMP are:

How to create a custom palette(with the correct number of entries for gif format)  for a given image.
How to export the image as gif using that palette.

Must dash.......
EDIT:
this might help
[http://gug.criticalhit.dk/tutorials/tomcat15/](http://gug.criticalhit.dk/tutorials/tomcat15/)

[http://www.esteveb.com/TutorialsEn/Gimp-Palette-Based-Images](http://www.esteveb.com/TutorialsEn/Gimp-Palette-Based-Images)

---

### Post by DaveMcC on 2011-04-07
post them as a jpeg, I came across this years ago, its some thing to do with "I can't remember" but all we done back then was to post all photos etc up as jpegs, for web sites we would go to image size and change it to suit, eg 240 X 160 pixels never had to go bigger than 480 X 640, and you can do that with gimp


hope this helps

Dave

---

### Post by suomalainen on 2011-04-07
It's not Linux Ubuntu but this took care of the problem once and for all.

Within the Format Menu on the top is "Web Options" which opens up on the
left side and at the bottom of that pane is "More Web Options". Click that
and under the "Web" tab, put a check mark on "Allow PNG as a graphics format
to improve graphics quality"

You will then have to go back to the jpeg or gif version of your photos
and/or gradient and save them as a .png. You can do this by right-clicking
on the graphic/photo and choosing "Save as Picture". Them navigate to where
you want to save it, name it, and in the "Save as type" drop-down box, select.png.

Carefully replace all the pictures/graphics with the .png version and you
should be seeing more clearly

---

### Post by Zimmer on 2011-04-07
> **DaveMcC said:**
> post them as a jpeg, I came across this years ago, its some thing to do with "I can't remember" but all we done back then was to post all photos etc up as jpegs, for web sites we would go to image size and change it to suit, eg 240 X 160 pixels never had to go bigger than 480 X 640, and you can do that with gimp


hope this helps

Dave

It would help except that jpg does not handle transparency, but png does...

---

