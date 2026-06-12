---
title: "unable to copy a .py file to"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by aszxcv on 2010-06-29
/usr/local/lib/python2.5/site-packages

i copy file from elsewhere but when i go to paste it in /usr/local/lib/python2.5/site-packages it doesnt let me paste it in

---

### Post by RetchingRabbit on 2010-06-29
You don't have user level write permissions to /usr/bin.
Use the terminal and sudo.

---

### Post by aszxcv on 2010-06-29
how do i this?

---

### Post by hackerseraph on 2010-06-29
enter the following in terminal

```
sudo nautilus
```

---

### Post by aszxcv on 2010-06-30
i did that but i still am not able to put file where i want to put it. i am getting frustrated because i am trying to learn python but i cant accomplish my task

---

### Post by aszxcv on 2010-06-30
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6607): WARNING **: Unable to add monitor: Operation not supported

---

### Post by oldfred on 2010-06-30
Usually sudo works but for graphical applications you are supposed to use gksudo so this may the when you have to use it.

gksudo nautilus

But be careful when in this superuser mode do not copy or delete other files as you have to capability to cause major damage.

if you do it from command line 

sudo cp source dest

---

