---
title: "IrfanView analog for Linux?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-04-05
Is there an IrfanView analog for Linux? Starting Gimp for rotating a single picture is quite heavy on the 256 MB of RAM I can spare for a second PC. Maybe you know some good lightweight image manipulation app?

---

### Post by Vaphell on 2009-04-05
default picture browser can rotate images just fine :-)

---

### Post by Rumtscho on 2009-04-05
All right, bad example; I want to be able to reduce colour depth, or change brightness/contrast etc., especially in a batch mode. IrfanView can even apply simple filters like Sharpen, and still it is only 1.5 MB after installation, and starts as quick as this default image browser.

---

### Post by northwestuntu on 2009-04-05
irfanview ran good in wine last time i used it.  one of the few programs i really miss from windows is irfanview.  used that for so long in windows ):P

---

### Post by krendar on 2009-04-05
> **Rumtscho said:**
> All right, bad example; I want to be able to reduce colour depth, or change brightness/contrast etc., especially in a batch mode. IrfanView can even apply simple filters like Sharpen, and still it is only 1.5 MB after installation, and starts as quick as this default image browser.

If you need to repeatedly do the same operation on many pictures perhaps you should take a look at ImageMagick:

[http://www.imagemagick.org/script/index.php]("http://www.imagemagick.org/script/index.php")

It is available via Synaptic (if its not installed by default). As you can see on the site I linked it is not a GUI application, you need to write a small script and run, but its very fast and once you stored your script you can keep running it if you need to process more pictures.

Hm, actually when I read the site there are some interfaces available, but frankly I don't know how good they are.

---

### Post by lovinglinux on 2009-04-05
If you need to organize and edit photo collections, then digiKam is the best tool I'm aware of.

If you just need a batch converter/editor, then try Phatch. Is pretty simple to use and you don't have to open the images. Just drag the files from nautilus into Patch and it will batch convert format, size, brightness and other stuff.

Both programs are in the repos.

---

### Post by gandaran on 2009-04-05
try [fotoxx]("http://kornelix.squarespace.com/fotoxx/"), you can get a .deb package from [getdeb]("http://www.getdeb.net/")

---

