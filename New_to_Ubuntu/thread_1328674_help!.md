---
title: "help!"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by mikhaell on 2009-11-16
i am a newbie with ubuntu 9.10. while trying to fix a problem with my mouspad (i have an eee) i must have typed something wrong on the "xorg.conf" and now grphics won't load! it sks for name and password nd then gives a terminal-like screen. What do i do?!

---

### Post by MonoDeem on 2009-11-16
X.org is reconfigurable:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by arashiko28 on 2009-11-16
while you find your video conf when you enter to configure xorg change the video driver for VESA , it's like a generic, after you know you video conf go back and change it.

---

### Post by sandyd on 2009-11-16
> **mikhaell said:**
> i am a newbie with ubuntu 9.10. while trying to fix a problem with my mouspad (i have an eee) i must have typed something wrong on the "xorg.conf" and now grphics won't load! it sks for name and password nd then gives a terminal-like screen. What do i do?!
login using your username and password.
then type this in
```

sudo dpkg-reconfigure  --pligh xserver-xorg

```

---

### Post by kansasnoob on 2009-11-16
> **MonoDeem said:**
> X.org is reconfigurable:

```
sudo dpkg-reconfigure xserver-xorg
```

While I have no answer for the OP would you care to elaborate?

Karmic has no such file to my knowledge.

Please elaborate.

---

### Post by kansasnoob on 2009-11-16
> **carlee said:**
> login using your username and password.
then type this in
```

sudo dpkg-reconfigure  --pligh xserver-xorg

```

"pligh"?

or "phigh"?

Neither works on Karmic.

---

### Post by kansasnoob on 2009-11-16
You might want to go back to your previous version and let the dust settle from this:

[http://www.itwire.com/content/view/28574/1141/](http://www.itwire.com/content/view/28574/1141/)

---

### Post by MonoDeem on 2009-11-16
> **kansasnoob said:**
> While I have no answer for the OP would you care to elaborate?

**By default **Karmic has no such file to my knowledge.

Please elaborate.

Quote edited.

---

### Post by mikhaell on 2009-11-16
it says that "pligh" is an unknown option. any other choices? any way to get to my desktop???

---

### Post by kansasnoob on 2009-11-16
> **MonoDeem said:**
> Quote edited.

So please offer a new or edited file!

The OP needs it badly!

---

### Post by kansasnoob on 2009-11-16
> **mikhaell said:**
> it says that "pligh" is an unknown option. any other choices? any way to get to my desktop???

Should be "phigh" which just means high priority but I have serious doubts.

---

### Post by mikhaell on 2009-11-16
ok kansasnoob, how do i downgrade from 9.10 back to 9.04? in fact, how do i do anything right now?

---

### Post by MonoDeem on 2009-11-16
> **mikhaell said:**
> ok kansasnoob, how do i downgrade from 9.10 back to 9.04? in fact, how do i do anything right now?

```
sudo rm /etc/X11/xorg.conf
sudo shutdown -r now
```

---

### Post by kansasnoob on 2009-11-16
> **mikhaell said:**
> ok kansasnoob, how do i downgrade from 9.10 back to 9.04? in fact, how do i do anything right now?

I'm clueless. I'm aware of the problems but have no idea how to solve them.

You can't "downgrade" to a previous version, only reinstall.

I'd listen to MonoDeem and see what he comes up with.

He seems to be confident and I'd trust him.

---

### Post by mikhaell on 2009-11-16
MonoDeem, i am in the desktop thanks! is ther anything i should do once i am here, or should i continue as if nothing happened?

---

### Post by MonoDeem on 2009-11-16
> **mikhaell said:**
> MonoDeem, i am in the desktop thanks! is ther anything i should do once i am here, or should i continue as if nothing happened?

You should be just fine.

---

