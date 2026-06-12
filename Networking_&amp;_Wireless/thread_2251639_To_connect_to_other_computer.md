---
title: "To connect to other computer"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by Peter_R._Larsen on 2014-11-05
Hello all

Is it possible to connect to computer to computer or laptop to computer or computer raspberry pi?

What I have in mind is monitoring to use my laptop and raspberry using face detector to other computer/raspberry.

Is there like face detection sofware for linux?

Thanks

---

### Post by TheFu on 2014-11-05
Sure, you can hop from system to system to system to system using ssh. These are non-graphical connections. Any system you want to connect with just needs openssh-server running and network access to whatever port you've decided to run that on. This is fairly standard stuff for UNIX/Linux.

Don't know anything about face detection and permissions on any system will determine whether a webcam is accessible or not. Connecting face detection to login credentials is problematic for many reasons. Android tried this and it only works in very controlled situations. In a home environment, with nothing important, I might use it on a leaf system with ZERO permissions to any other systems in the house.  That way, you can just provide any guests with a photo of yourself and they can gain access.

Fingerprints concern me more ... when someone takes a photo, they get my face and can walk away.  I hope they just want an image of my finger print and don't want the real thing. ;(    Don't get me thinking about iris-based authentication.

---

### Post by Peter_R._Larsen on 2014-11-05
> **TheFu said:**
> Sure, you can hop from system to system to system to system using ssh. These are non-graphical connections. Any system you want to connect with just needs openssh-server running and network access to whatever port you've decided to run that on. This is fairly standard stuff for UNIX/Linux.

Don't know anything about face detection and permissions on any system will determine whether a webcam is accessible or not. Connecting face detection to login credentials is problematic for many reasons. Android tried this and it only works in very controlled situations. In a home environment, with nothing important, I might use it on a leaf system with ZERO permissions to any other systems in the house.  That way, you can just provide any guests with a photo of yourself and they can gain access.

Fingerprints concern me more ... when someone takes a photo, they get my face and can walk away.  I hope they just want an image of my finger print and don't want the real thing. ;(    Don't get me thinking about iris-based authentication.

Just thought something which maybe impossible
Will try those though

Thanks

---

### Post by TheFu on 2014-11-05
Check out **gpg-agent** and **ssh-agent**.

---

### Post by Peter_R._Larsen on 2014-11-05
> **TheFu said:**
> Check out **gpg-agent** and **ssh-agent**.

will do

---

### Post by steeldriver on 2014-11-05
You might want to look at OpenCV for the face detection --> [http://docs.opencv.org/trunk/doc/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html](http://docs.opencv.org/trunk/doc/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html)

---

