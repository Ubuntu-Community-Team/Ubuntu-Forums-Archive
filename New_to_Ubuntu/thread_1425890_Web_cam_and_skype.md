---
title: "Web cam and skype"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by jdc158 on 2010-03-09
So my web cam works fine with Cheese but not with skype. When I try to test the webcam it doesn't do anything. My webcam is a creative VF-0040 and im running skype 2.1 beta. How can I fix this?

---

### Post by ajgreeny on 2010-03-09
Instead of starting skype with the command "skype" in your startup programs, if that's how you start it at bootup, or from your menu, try starting it with the following shell script saved as **skypestart.sh** in your home
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype
```
Make that file executable and point a "startup program" command at it with full pathway ie, in the command box box type:  **/home/user/skypestart.sh**

If you are using a 64 bit ubuntu install you will need to change the shell script to 
```
#!/bin/bash
export LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so
skype
```

---

### Post by jdc158 on 2010-03-09
So that first command worked but I'm not sure that I understand the second half.

---

### Post by spiderbatdad on 2010-03-09
you can create a new launcher to point to your skype start up script. There is an old example from a little over a year ago here, but it is still good.:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1026188](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1026188)

---

