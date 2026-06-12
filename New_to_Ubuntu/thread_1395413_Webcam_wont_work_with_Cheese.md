---
title: "Webcam wont work with Cheese"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-31
Hello friends

I've been searching online how to get webcam to work with cheese and skype but so far hit a wall.My webcam works fine with Ekiga and guvcview but i cant get it to work with Cheese nor Skype.If i run a test with Plugin:Video for Linux(v4l) it fails but not with Video for Linux
(v4l2).Pipeline v4l2src.The weird thing is that same webcam works fine running cheese and skype in ubuntu 8.04.Can anyone help me get it set up to work with Cheese or Skype?Thanks

---

### Post by Methuselah on 2010-01-31
Try running skype with this command in a terminal.

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by manny43 on 2010-01-31
running skype with that command in terminal same result

---

