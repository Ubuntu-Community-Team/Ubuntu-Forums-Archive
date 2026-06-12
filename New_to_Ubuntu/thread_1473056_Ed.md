---
title: "Ed"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by SpeedGraphicFanatic on 2010-05-04
I just came back from Costa Rica Where I used my Canon 20D, in camera raw. I filled up my 2GB memory card so I had someone transfer the information to a DVD. One of the DVD's is giving me problems. When I try to open the images in Digital Photo Professional, the images do not upload. The little hour glass just keeps showing fore ever. I can't even open the Jpgs in Photoshop. When I try to do that each of the individual image windows shows a paddle lock and a giant question mark. The DVD that was used says "DVD-R47P 16Z Printable Video 120 Min.

---

### Post by cariboo on 2010-05-04
It sounds like a permission issue, can you copy the images to your hard drive in root mode. Press Alt-F2 and type:

```
gksu nautilus
```

the above command will open the file manager as root and allow you to copy the images from the DVD.

---

### Post by no2498 on 2010-05-05
would he not need the raw file format that is a gimp add on ?

---

