---
title: "converting jpg files to png or svg files"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by knuckle dragging monkey on 2009-06-08
Hello, I am trying to download some cursors into my cursor selection. but only png files seem to be working. so is there a way to convert a jpg or another type of file to png file type. Thank you.

---

### Post by keplerspeed on 2009-06-08
Yes. Open the image with the gimp image editor. Then 'save as' as the required format!

---

### Post by knuckle dragging monkey on 2009-06-08
how can i find gimp editor. I am sorry but i am a complete noob.

---

### Post by knuckle dragging monkey on 2009-06-08
ok i have found it but how do i add that file to convert it.

---

### Post by Fully216 on 2009-06-08
Applications > Graphics > GIMP Image Editor

If it is not there, you can install it in synaptic, or by selecting it in Applications > Add/Remove...

---

### Post by Fully216 on 2009-06-08
Simply click open, and locate the saved jpg file.

---

### Post by knuckle dragging monkey on 2009-06-08
ok so save it to my desktop then open the gimp editor.then what ? i have 3 different boxes that pop up.

---

### Post by Fully216 on 2009-06-08
Click File > Open

Which gives you a menu entitled Open Image

Locate the jpg file you want to convert and click Open

The click File > Save As

Which will give you a menu entitled Save Image

At the bottom, select Select File Type (By Extension) and highlight PNG Image.  You will notice this changes the extension from *.jpg to *.png

Click Save and you are done!

---

### Post by knuckle dragging monkey on 2009-06-08
Thank you very much. i will try that.

---

### Post by knuckle dragging monkey on 2009-06-08
no ware in the gimp program does it say open image. i don't know what to do.

---

### Post by k_squired on 2009-06-08
Ubuntu should come with the gimp -  a fully featured processor.  Open them with the gimp, and save them as whatever format you want.

---

### Post by jolx on 2009-06-08
> **knuckle dragging monkey said:**
> no ware in the gimp program does it say open image. i don't know what to do.

It's under the 'File' menu and it's called 'Open...'

---

### Post by k_squired on 2009-06-08
You could also use eye of the Gnome, you know your defualt image viewer?  Open one up, check the about message to make sure it is eye of the Gnome, and then just do save as.

In gimp, go to file open.

---

### Post by keplerspeed on 2009-06-08
Try right clicking on the image in the file browser, and select open with gimp.

However, simply file>open should allow you to open the file. As jolx mentioned above.

---

### Post by knuckle dragging monkey on 2009-06-08
ok i clicked file then the open image came up. then i clicked on the file i want to convert .but there is no save as button.

---

### Post by knuckle dragging monkey on 2009-06-08
ok i  figured it out . i deleted it and then downloaded it over. and so i had to delete it from my hidden files. Thank you all very much. and i apologize from being such a noob.

---

### Post by mbsullivan on 2009-06-08
Another simple way to do this is to use the "convert" utility. It must be used from the command line, but can be a real time saver (especially if you have many files to convert).

To use it:

```
sudo aptitude install imagemagick
[go to directory containing the files]
convert [name].jpg [name].png
```

Creating SVG files out of raster images (such as .jpeg images) is generally not a good idea. SVG is a vectorized image format, and there are no really good tools for vectorizing a raster image.

Mike

---

