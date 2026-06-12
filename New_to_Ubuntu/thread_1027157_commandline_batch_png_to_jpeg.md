---
title: "commandline batch png to jpeg"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by djbushido on 2009-01-01
I would like to convert a few hundred png's to jpeg's. I would like just a command-line tool to create a lossless jpeg of the png, and I need to be able to do it on a few hundred pictures. Thanks a lot!

---

### Post by Coder543 on 2009-01-01
try the 'convert' program from the [imagemagick]("apt:imagemagick") package.

---

### Post by unutbu on 2009-01-01
```
sudo apt-get install imagemagick
mogrify -quality 100 -format jpg *.png
```

JPEG is not really meant as a lossless format. Using -quality 100 typically makes the file quite large.

---

