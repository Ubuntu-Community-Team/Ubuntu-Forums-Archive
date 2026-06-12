---
title: "Camera Metadata"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Ahunt on 2011-07-02
Photos taken by cameras or scanned by some scanners have metadata attached to them that gives information on when the photos were taken, camera type, the shutter speed, f-stop and other similar information. 

More complex file managers like Nautilus can read and display this data but Lubuntu's PCManFM does not. 

I was wondering if there is a command line instruction that can show the metadata for a particular image file?

---

### Post by wolfen69 on 2011-07-02
Exiv2 [http://www.exiv2.org/](http://www.exiv2.org/) which should already be installed for you.

---

### Post by Ahunt on 2011-07-02
Thanks for that quick reply! Exiv2 is not installed by default in Lubuntu, but let me check it out and see if it can do the job!

---

### Post by Ahunt on 2011-07-03
Okay I had a change to test it out and it works! That you for suggesting Exiv2!

For anyone who wants to use this utility you just have to ensure Exiv2 is installed and then to read image metadata you just enter into a terminal:

```
$ exiv2 ~/pathtofile
```

and it will output the metadata on the image file.

---

