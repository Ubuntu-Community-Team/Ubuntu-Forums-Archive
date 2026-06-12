---
title: "convert jpg to eps"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-02
I am using Ubuntu 10.04.
I was wondering if there was any method/ software where I could convert from a popular image format(jpg, png, eps) to another and vice versa. specifically jpg to eps.

---

### Post by jtarin on 2010-08-02
Plenty of [online ones]("http://www.google.com/webhp?hl=en&tab=nw#hl=en&source=hp&q=jpg+to+eps+online&aq=3&aqi=g-c1g5g-c1g2g-c1&aql=&oq=&gs_rfai=&pbx=1&fp=fb0bee69b5aae820") before you download and install

---

### Post by gaurish108 on 2010-08-02
Thank you for the reply. I also just go to know imagemagick is also used fro doing the file conversion.......cheerss!

---

### Post by Groucho Marxist on 2010-08-02
My sister is a graphic designer who uses Adobe CS4 at work; yes, I realize that is not a FOSS program. However, we have to start somewhere to solve this question.

She says that, "The best program available for converting JPG to EPS would be Adobe Illustrator. At least CS2 has a feature called "live trace" which will convert the pixels into a vector image." She warns, "Be advised; there is no editing a live image with a pen tool in Illustrator." 

In terms of a comparable Linux version of Illustrator, Inkscape may accomplish this goal as it deals with SVG (Scalable Vector Graphics) and (as far as I am aware of) will be able to convert from JPG to EPS.

---

### Post by gaurish108 on 2010-08-02
Thank you for the reply. Ink scape indeed seems to be very powerful for working with images. 

Image conversion I just found can also be done with GIMP, simply by doing 'save as' and the name.file extension. 

What would be more convenient is if I could include some sort of a command in the latex file which does this document conversion for me automatically. That would save a lot of time spent in opening images with softwares like GIMP and doing file conversion. especially when when images are spread across many folders.

---

### Post by jtarin on 2010-08-02
You could possibly make a [script for imagemagik]("http://www.imagemagick.org/Usage/") to run on your files.
```
./imagemagik-convert-eps filename
```

---

### Post by -kg- on 2010-08-02
You can also use GIMP.

Load the image into GIMP, select "File/Save As", and when the Dialog box pops up, open the "Select File Type (by Extension)" box (by clicking the "+" sign), and select the file type from the list.  It will ask you to Export first (sometimes), then will save the image in the selected format.

It doesn't just put an extension on it; it actually converts the image to that format.  When you open the file in GIMP, it will ask you to import it, as the image has been converted.  Also, all "Properties" show it as that type of file.

<Edit>  Guess I should ***_read_ _all_ _the_ _posts_*** before I post:

> Image conversion I just found can also be done with GIMP, simply by doing 'save as' and the name.file extension. 

#-o

---

### Post by jtarin on 2010-08-02
> **-kg- said:**
> 
<Edit>  Guess I should ***_read_ _all_ _the_ _posts_*** before I post:#-o
Maybe not all.:p

---

