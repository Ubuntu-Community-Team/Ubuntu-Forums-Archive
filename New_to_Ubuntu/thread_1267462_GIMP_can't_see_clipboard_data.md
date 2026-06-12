---
title: "GIMP can't see clipboard data"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-15
When copying images to clipboard, or using print screen, etc. The GIMP can't see the picture data (IE: It says that there is no image data.) This happens even in GIMP 2.7.1

---

### Post by stderr on 2009-09-15
If you drag an image file onto the canvas, or if taking a screenshot, drag the screenshot image GNOME gives you onto the canvas, that should work. I think GIMP doesn't bother to read a file if you've just copied a file path onto the clipboard, as opposed to the actual binary image data.

---

### Post by coldReactive on 2009-09-15
> **stderr said:**
> If you drag an image file onto the canvas, or if taking a screenshot, drag the screenshot image GNOME gives you onto the canvas, that should work. I think GIMP doesn't bother to read a file if you've just copied a file path onto the clipboard, as opposed to the actual binary image data.

That's not what I'm trying to do.

[http://www.freedigitalphotos.net/image/s_garden-gnome.jpg](http://www.freedigitalphotos.net/image/s_garden-gnome.jpg)

Right-click the above image when viewing it, and click Copy Image (assuming you use firefox.) Then hit CRTL+V in GIMP. I get the error stating there is no image data on the clipboard.

---

### Post by oldfred on 2009-09-15
Worked fine for me.

In ubuntu I found anything I copy if I close the window I am copying from before I paste the copy has disappeared. If I do not close the window I am copying from it copies just fine.

---

### Post by coldReactive on 2009-09-15
> **oldfred said:**
> Worked fine for me.

In ubuntu I found anything I copy if I close the window I am copying from before I paste the copy has disappeared. If I do not close the window I am copying from it copies just fine.

Problem is, the error happens even though I leave Firefox open, or if I hit copy to clipboard when taking a screenshot of the desktop. I often get this a lot.

---

### Post by Ms_Angel_D on 2009-09-15
try installing Parcellite and using it, it's a clipboard manager.

you can find it in add/remove programs or synaptic.

or you can run this command to install it:

```
sudo apt-get install parcellite
```

or you can simply click here-> [Install Parcellite]("apt://parcellite")

---

### Post by coldReactive on 2009-09-15
> **Ms_Angel_D said:**
> try installing Parcellite and using it, it's a clipboard manager.

you can find it in add/remove programs or synaptic.

or you can run this command to install it:

```
sudo apt-get install parcellite
```

or you can simply click here-> [Install Parcellite]("apt://parcellite")

Had the problem even before with my decked out install of Ubuntu, with parcellite.

---

### Post by jan.ptacek on 2009-12-08
actually, after quiting parcellite the paste feature has resumed working on my karmic ubuntu and with inkscape!

---

