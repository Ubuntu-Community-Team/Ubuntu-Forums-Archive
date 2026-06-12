---
title: "reducing the  size of photos."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by gordon33 on 2009-01-15
Hello

I am usinf g a 7.10 version of unbutu.  How can I reduce the size of photos and resave Them.  I mean less bits or bites.

Gordon Webb

---

### Post by 73ckn797 on 2009-01-15
> **gordon33 said:**
> Hello

I am usinf g a 7.10 version of unbutu.  How can I reduce the size of photos and resave Them.  I mean less bits or bites.

Gordon Webb

Most photo editing programs allow you to resize photos. The smaller the size the less data = less bytes.

A 640X480 photo size is usually less than 150Kb in size and possibly under 100Kb.

---

### Post by HermanAB on 2009-01-15
Open the photo with The Gimp and click File Save As, select JPEG.  Otherwise, use Image Magick.

Cheers,

Herman

---

### Post by flaggh on 2009-01-15
install the nautilus-image-converter plugin
```
sudo apt-get install nautilus-image-converter
```

Then, when you right click on an image in nautilus, there will be an option to resize.

---

### Post by cariboo on 2009-01-15
Have a look at [Imagemagic]("http://www.imagemagick.org/script/index.php"), it will allow you to do batch resizing and a lot more. Imagemagick is available in the repositories.

Jim

---

### Post by laffinet on 2009-01-15
[Phatch]("http://photobatch.stani.be/") is another convenient batch processor that lets you do quite a range of editing.

---

### Post by bodhi.zazen on 2009-01-15
If you are interested in a command line tool, check out convert.

man convert

Quite powerful and does a nice job.

---

### Post by gordon33 on 2009-01-18
Thank you with all the help I was able to reduce the size of the photos several diffrent ways.

Thanks again

Gordon33

---

