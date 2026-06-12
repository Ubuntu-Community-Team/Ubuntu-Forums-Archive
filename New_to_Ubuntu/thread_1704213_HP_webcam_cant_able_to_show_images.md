---
title: "HP webcam cant able to show images"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by go2xraj on 2011-03-10
HP web cam is not showing images in the desktop but it is viewed by the other end.

Please help me

---

### Post by Kirboosy on 2011-03-10
What program are you using?

---

### Post by go2xraj on 2011-03-10
skype

---

### Post by Kirboosy on 2011-03-10
If you right click on the window that has your call information (the other persons video) there should be an option like "display my self portrait" I can't remember off the top of my head but if that box isn't checked then you won't be able to see yourself.

---

### Post by go2xraj on 2011-03-10
but i cant able to see my self in the test video also

---

### Post by Kirboosy on 2011-03-10
Try running this command in Terminal ```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Found it on [this thread]("http://ubuntuforums.org/showthread.php?t=997807")

---

