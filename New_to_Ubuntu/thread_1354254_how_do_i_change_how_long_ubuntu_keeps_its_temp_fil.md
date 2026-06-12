---
title: "how do i change how long ubuntu keeps its temp files for?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by dantakeoff on 2009-12-13
i have a really slow internet connection and cannot afford the time or bandwidth to download the same things twice, which i often need to do, for instance youtube videos that i refer to again, instead of being readily available in my temp folder have been deleted and now i have to download them again. i need to change the amount of time ubuntu keeps these files for, for instance 1 week or so... hard drive space is not a problem, but limited 3g bandwith is....
any suggestions?

---

### Post by ajgreeny on 2009-12-13
Having loaded the youtube page and downloaded the video, you can copy the Flashx#x#x#x file from /tmp to another folder in your home, otherwise, once you close the youtube page, the Flashx#x#x#x# file will be removed from /tmp.

I do it with a script file:-
```
#!/bin/bash
cp /tmp/Flash* /home/username/Movies
```which sits in my panel.  One click and it's done.  There are also firefox add-ons available to do this, but I think my way is easier.

---

### Post by presence1960 on 2009-12-13
for vids try the firefox addon Fast Video Download which allows you to save them to disk

---

### Post by dantakeoff on 2009-12-15
thanks man, that helps but i need it to do it automatically...any scripts out there to get it to save the flash file for one week?
your help is appreciated....

---

