---
title: "Microsoft NX-6000"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by v4vishal.patel on 2010-02-15
Hi Guys
I am a absolute beginner and trying to make my nx-6000 working with skype
I have tried to search the forum but can not find any solutions. please help
BTW already tried updating to V4l2 and it works with Ekiga but not with Skype.

help !!!! help !!!! help !!!!

---

### Post by Julita on 2010-02-15
Try to start Skype from the terminal with:
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
see what happens. If it doesn't help, try
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by v4vishal.patel on 2010-02-15
Hey Julita,
thanks a bunch for the quick reply. first command works but when I make a call, it just drops out and skype shuts down by itself.

---

### Post by Julita on 2010-02-15
Which Skype version do you use? If it is the latest one, then it has some issues. Please try the previous version. You can find it here: [http://rapidshare.com/files/351065540/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb.html](http://rapidshare.com/files/351065540/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb.html)

---

### Post by v4vishal.patel on 2010-02-16
Tried with the version you suggested as well. I am getting following error on terminal
"libv4l2 : error converting /decoding frame data: v4l-covert : error parsing JPEG header : Not a JPG file ?
 
"libv4lconvert : Error decomprassing JPEG: error: more than 63 AC components (70) in huffman unit
Segmentation fault"
 
and it just shuts skype

---

### Post by Julita on 2010-02-16
Did you start the older version with
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
too?
Have you tried the camera with other applications? Try
```
luvcview -w -s 960x720
``` in a terminal. If you can see the picture, then it is skype's issue. You can also try program cheese to check video. Your camera is generally supported by Ubuntu, but it really can be skype's trouble. If not a single program shows video, you have to follow the instructions here: [http://agert.homelinux.org/blog/index.php/Microsoft_Lifecam_NX-6000](http://agert.homelinux.org/blog/index.php/Microsoft_Lifecam_NX-6000)

---

