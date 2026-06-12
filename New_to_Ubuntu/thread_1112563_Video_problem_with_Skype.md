---
title: "Video problem with Skype"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-03-31
I have this script to run Skype on Ubuntu/Xubuntu and it has worked fine before.

```
#!/bin/bash

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
```

But today I tried to test the webcam and Skype just closes and quits. There has been several updates since I used my webcam, could it the reason why it is not working?

Anyone has a solution so it could work again? Thanks!

---

### Post by willz06jw on 2009-04-22
Make sure that your Skype settings are pointing to the correct device.  I know it sounds simplistic, but I found a problem with those settings when I had the same issue a few months ago.

---

