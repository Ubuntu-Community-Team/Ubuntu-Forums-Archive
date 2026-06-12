---
title: "No Video Feedback on Skype"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by boriszerussian on 2008-12-17
I just ran a reinstall of ubuntu and now I am getting no video feedback from Skype.  The person that I connect with can see my video feed, but I cannot see either one.  Ekiga worked, but cheese wouldn't even load.  I would appreciate any help I can get.

---

### Post by spiderbatdad on 2008-12-17
make sure your fresh install is updated. ```
sudo apt-get update && sudo apt-get upgrade
```The fix for libv4l-0 has been released, but from here I still have to run skype with LD_PRELOAD.```
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

```Track the history of the bug here: [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

---

### Post by boriszerussian on 2008-12-17
I went through and tried to get all of my old settings back, this is the only issue I still have.  When I entered the second command there it did open Skype, but it also gave this message about five times:

ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

---

