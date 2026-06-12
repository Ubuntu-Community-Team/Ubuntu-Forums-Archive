---
title: "how do you join / stich jpeg files together?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by stinger30au on 2009-05-10
here is my situation

im scanning some magazine i have from 1983 - yes, thats right 26 years old

the magazines are longer then A4 and are so long infact they over hang the length of my scanner by about 1.5 inches or there abouts

the width is ok, it is a4 so no worries there

what i want to do is before they are totally decayed and unreadable is preserve them to pdf eventually.

i can scan about 2/3's of the page and then save that image and move the magazine up and scan the final part of the page and so on and so forth. this is the easy bit

im not sure how to join the 2 scan together to make one single page. i have thought about gimp, but to be honest i have not used something like that since i used coco-max by colorware on my tandy coco 1 in about 1985 as i have had no need to... untill now.


the other idea i had was maybe a photo stich type program like some cameras use to join multiple photos together to make a jiant portrait, or better yet something like this but on a web site and i can upload the pages there and use wysiwyg to make sure its all ok.

any thoughts, ideas, feedback would be greatly appreciated

thanks

---

### Post by HereInOz on 2009-05-10
Gimp would be a solution.  You could crop and resize both images to fit, and then put one onto the other using a second layer.  

You would need to do some reading up on how to use layers in GIMP but it would certainly do the job. GIMP would create an image file - to my knowledge it will not save as a PDF directly.  

You would need to create the image file and then print that to a PDF, or save it as PS file then use ps2pdf to create the PDF from the postscript PS file.

---

### Post by unutbu on 2009-05-10
There is a package in the official repositories called **hugin** that can help you stitch photos together. See
[http://hugin.sourceforge.net/](http://hugin.sourceforge.net/) for documentation, tutorials and screenshots.

---

### Post by stinger30au on 2009-05-10
thanks for the feedback guys

---

### Post by stinger30au on 2009-05-25
this web site gives an inssite on how to stick the mags together manually

[http://homepage.ntlworld.com/lynnfo/educatio/scanning/scannn02.html](http://homepage.ntlworld.com/lynnfo/educatio/scanning/scannn02.html)

---

### Post by linux000019 on 2009-05-25
i don't know if linux has " ifranview ", this program has done everything i wanted pretty painlessly and its free; for windows anyway...

---

### Post by robert shearer on 2009-05-25
I have found fotoxx to be easy to use....

[http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/)

and it is in the Jaunty Repos(EDIT on another machine so cannot check this so may be wrong about the repo)

---

### Post by unutbu on 2009-05-25
Wow! Thanks for the heads-up on fotoxx, robert shearer.
I'm impressed that it can work on 16-bit color images and do photo stitching and unbending.

Have you used hugin as well? Do you have an opinion on how they compare?

Unfortunately, it does not appear to be in the repos: [http://packages.ubuntu.com/search?keywords=fotoxx&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=fotoxx&searchon=names&suite=jaunty&section=all)

---

### Post by HermanAB on 2009-05-25
ImageMagick of course:
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by robert shearer on 2009-05-26
> Unfortunately, it does not appear to be in the repos: [http://packages.ubuntu.com/search?keywords=fotoxx&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=fotoxx&searchon=names&suite=jaunty&section=all)

Yes, though fotoxx site has a deb package for ubuntu..

[http://kornelix.squarespace.com/packages/](http://kornelix.squarespace.com/packages/)

and click on the appropriate package
 eg,....   fotoxx-6.9.2-i686.deb for  32 bit Ubuntu


and if you like  the simplicity of **fotoxx** then try **phatch** to complement it. (that is in the repos)

---

### Post by stinger30au on 2009-05-27
> **linux000019 said:**
> i don't know if linux has " ifranview ", this program has done everything i wanted pretty painlessly and its free; for windows anyway...

it works with wine

i ill try that

---

### Post by stinger30au on 2009-05-27
well i have done more hunting and if i was using windows i could use these follow products


[http://www.vextrasoft.com/rasterstitch.htm](http://www.vextrasoft.com/rasterstitch.htm)


[http://www.arcsoft.com/products/scannstitch/](http://www.arcsoft.com/products/scannstitch/)


now if only i could find freeware/opensource versions of these

---

### Post by stinger30au on 2009-05-28
well finally after much searching i have found the settings to make "autostitch" make the pages join flat

[http://karolisl.blogspot.com/2006/04/scanning.html](http://karolisl.blogspot.com/2006/04/scanning.html)

---

