---
title: "jpeg rgb conversion to cymk? Howto?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by packrat on 2009-02-09
Anyone know how to convert a jpeg from red,green, blue to cymk for off-set printing? Thanks.

---

### Post by punx45 on 2009-02-09
i would guess  that the GIMP can do it.

---

### Post by packrat on 2009-02-09
Wish gimp could make the conversion to cmyk but it can't...

---

### Post by niteshifter on 2009-02-09
Hi,

ImageMagick (package name: imagemagick) has the utlities for this. Example:

```
convert inputfile -colorspace cmyk outputfile
```

After installing, point your browser to:

```
file:///usr/share/doc/imagemagick/index.html
```

as this is a very versatile package.

---

### Post by packrat on 2009-02-11
Thanks.

File is on desktop...here's what I enter in terminal...

$ convert img_0505.jpg -colorspace img_0505.tiff
convert: unable to open image `img_0505.jpg': No such file or directory.
convert: option requires an argument `-colorspace'.

So, what's my problem? And furthermore, is a tiff file what I want to offset print? Also, is one able to rename the file one converts to without changing the original file?

---

### Post by mc4man on 2009-02-11
> So, what's my problem
Purely on the command (not what your doing

If the file is in your home folder than 
> convert img_0505.jpg
will work

If it's on your desktop you need to provide path
> convert ~/Desktop/img_0505.jpg
For the output 
> img_0505.tiff
That will save to your home folder, if you wish somewhere else put path in front of filename

> convert: option requires an argument `-colorspace'.
You didn't supply an arg. as in prior post cmyk


```
convert ~/Desktop/img_0505.jpg -colorspace cmyk img_0505.tiff

```

If you save to same dir. with same extension, then you should alter the name slightly

```
convert ~/Desktop/img_0505.jpg -colorspace cmyk ~/Desktop/img_0505-1.jpg
```

---

### Post by yther on 2009-02-11
> **packrat said:**
> ... And furthermore, _is a tiff file what I want to offset print?_ Also, is one able to rename the file one converts to without changing the original file?

If you're not sure, I suggest you ask the person or company you'll be giving the file.  They should be able to provide you the details they need, such as file type, resolution, etc.  Providing a file they don't want or can't use will just send you back to the drawing board.  :)

---

