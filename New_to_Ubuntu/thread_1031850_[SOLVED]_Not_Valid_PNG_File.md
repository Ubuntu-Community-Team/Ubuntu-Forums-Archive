---
title: "[SOLVED] Not Valid PNG File"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-01-05
Hey everyone. My sister made some picture in Paint Shop Pro 8 in Windows XP and somehow screwed it up saving it. It is supposed to be a PNG file, but nothing I throw at it will open the damn file. I've tried OpenOffice 3.0 Draw, GIMP, almost all of the image viewers in Ubuntu.

Is there any way to recover this file either finding a temporary, previous revision of the file on her computer (Windows XP)? Or is there something I can do in Ubuntu to fix the file?

I've tried changing the file to a .jpg, but that didn't solve it either. I also tried an online converter of the original PNG, but it doesn't recognize the file either. 

This is somewhat of an emergency for her because she needs it for tomorrow, and she will be going to sleep soon, so I will appreciate the hasty responses!

edit: Couldn't attach the file because it's larger than 900 something KB. I uploaded it to rapidshare and it is linked in a later post.

---

### Post by amauk on 2009-01-05
> **Lazy-buntu said:**
> I've linked the file below.no you haven't ;)

---

### Post by amauk on 2009-01-05
try changing the extension to .psp
that's the native format for paint shop pro
Gimp can read paint shop pro files

---

### Post by Lazy-buntu on 2009-01-05
Here's the rapidshare link:

[http://rapidshare.com/files/180210869/Recovery_Image.png.zip.html](http://rapidshare.com/files/180210869/Recovery_Image.png.zip.html)

---

### Post by Lazy-buntu on 2009-01-05
Attempt to open in GIMP as a .psp:

---

### Post by donkyhotay on 2009-01-05
If it was just a matter of having the wrong file extension (having a .png named as a .jpg) then GIMP sgould be able to figure things out and open it anyways. Lets see what can be done though, first of all can you post the results of
```
file name_of_file.png
```
where name_of_file.png is of course the name of your file.

---

### Post by inigomontoya on 2009-01-05
Fixed with IrfanView under wine.  I saved it as another png with higher compression to preserve quality.

[http://files.mint-space.com/getfile,20090106011226,Recovery%20Image.png.html](http://files.mint-space.com/getfile,20090106011226,Recovery%20Image.png.html)

---

### Post by Lazy-buntu on 2009-01-05
If you try to open the file as a .png you get the same error as the .psp (the same error picture attached above).

---

### Post by Lazy-buntu on 2009-01-05
> **inigomontoya said:**
> Fixed with IrfanView under wine.  I saved it as another png with higher compression to preserve quality.

[http://files.mint-space.com/getfile,20090106011226,Recovery%20Image.png.html](http://files.mint-space.com/getfile,20090106011226,Recovery%20Image.png.html)

Thank you, you're our hero!

Mind telling me how you did that?

---

### Post by inigomontoya on 2009-01-05
IrfanView usually opens everything.  I tried to open it with my standard IrfanView install and it refused.  It suggested I download the extra formats plugin.  I did, and voila.  FYI in the image information page it lists the compression as "ZLIB - LZ77" Whatever that is.  A PNG file should have "PNG - ZIP" compression.

---

### Post by amauk on 2009-01-05
it's a JPEG with a corrupted header
I've stripped the header out

[http://www.snoopy.force9.co.uk/001a.jpg]("http://www.snoopy.force9.co.uk/001a.jpg")

*edit*
too late...

---

### Post by Lazy-buntu on 2009-01-05
Thanks for the fast replies, you guys are good.

I don't know how she managed to screw up something as (seemingly) easy as saving a file.

In my opinion, this is one major reason why Ubuntu rocks: the awesome community. I think for saving this file she may let me set her computer up with Ubuntu. Anyway, thanks again guys.

---

