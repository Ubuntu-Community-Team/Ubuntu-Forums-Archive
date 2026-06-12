---
title: "How to implement a patch"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Excedio on 2010-05-17
Can someone please help me to figure out how to implement a patch for notify-osd? I have the patch, but I'm not sure what to do with it.

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508/comments/37](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508/comments/37)

> Here is the patch.

 You need to kill notify-osd and start the new one from the new source  code.

 notify-send does all the right thing by sending all the data through  dbus. On the other hand, notify-osd doesn't respect the "timeout" value  sent by notify-send and instead uses the default values.

 notify-send sends "-1" to denote "default timeout", when "-t" option  is "NOT" given. Otherwise, the user specified timeout value is sent. So,  what I do is use the default timeout values when "-1" is sent and the  user specified value otherwise.

 I'm not an active developer. So, my fixes might be broken. Please use  it with caution :)

I uploaded the patch as a .txt file type, however the original file is a .patch file type.

---

### Post by Excedio on 2010-05-19
Bump. Please?

---

