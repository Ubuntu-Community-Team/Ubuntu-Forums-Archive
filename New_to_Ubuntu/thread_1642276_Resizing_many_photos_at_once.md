---
title: "Resizing many photos at once"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by corncob on 2010-12-10
I have 30 digital camera photos, each 3 to 5 megs in size, and I need to reduce the size for emailing.  Is there any way to do this all at once rather than one at a time?  [http://www.picresize.com/](http://www.picresize.com/) was suggested but doesn't seem to work for me. I found a program in Synaptic (Mirage) that lines the pictures up but I still have to resize them one by one.

---

### Post by amjjawad on 2010-12-10
> **corncob said:**
> I have 30 digital camera photos, each 3 to 5 megs in size, and I need to reduce the size for emailing.  Is there any way to do this all at once rather than one at a time?  [http://www.picresize.com/](http://www.picresize.com/) was suggested but doesn't seem to work for me. I found a program in Synaptic (Mirage) that lines the pictures up but I still have to resize them one by one.

From Synaptic, type: nautilus-image-converter.

Mark for installation then apply.
Log out from Ubuntu, login back and that's all.

You don't need any program, just that plug-ins.
Work perfectly for me.

---

### Post by nothingspecial on 2010-12-10
Or install imagemagick and, aslong as they are in the same directory, do something like this
```

for p in *.jpg; do convert -resize 50% $p new_$p; done
```

---

### Post by philinux on 2010-12-10
Or gthumb can do it.

---

### Post by freesitebuilder on 2010-12-10
I use Phatch. (PHoto bATCH) First you set up the actions (resize, colour, etc) and then apply that set of actions to a batch of photos. Save the set of actions for future use if you want to.

---

### Post by chamira on 2010-12-10
Most sophisticated image manipulation progs allow you to create macros or 'actions'- a set of commands. These are then run against a folder or a set of open files. This is called 'batch processing'. 


Photoshop has a great ability to 'record' a sequence of actions as you preform them on one file, save it and run it against a whole folder - very powerful.

For Ubuntu I know Gimp has scripting ability but not sure how easy or hard it is and I can't test this out for you at the moment.

---

### Post by corncob on 2010-12-10
Thanks for all the replies!  The first thing worked just fine.

---

### Post by amjjawad on 2010-12-10
> **corncob said:**
> Thanks for all the replies!  The first thing worked just fine.

Glad to know it worked for you :)
Enjoy!

---

### Post by mbienek on 2010-12-10
Installed ImageMagik on Ubuntu 9.10
Tried to convert image and got the following:
convert: Wrong JPEG library version: library is 62, caller expects 70 `DSC_0001.JPG' @ error/jpeg.c/EmitMessage/235.
How do I update my JPEG library ?

---

### Post by richardandrews on 2011-03-15
Thank you, I've now got cairo-dock slider using a lot less cpu!

---

