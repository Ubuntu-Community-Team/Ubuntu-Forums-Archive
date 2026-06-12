---
title: "How to install OpenCV"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by ranjith19 on 2010-10-08
I tried apt-cache search opencv and I got results that did not include it.

---

### Post by lykeion on 2010-10-08
OpenCV is not a single appplication, it's a collection of libraries written in C and C++.
 
Here's install instructions for Ubuntu:
[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

Note: I had problems compiling examples using build_all.sh script but all I needed was to make it executable:```
chmod +x build_all.sh
```Open the file:```
gedit build_all.sh
```Then change the line```
if [ $# > 0 ] ; then
```to```
if [ $# -gt 0 ] ; then
```

To test a simple face detection:
```
./facedetect --cascade="/usr/share/opencv/haarcascades/haarcascade_frontalface_alt.xml" --scale=1.5 lena.jpg
```

---

### Post by ranjith19 on 2010-10-09
I will try. Thanks

---

