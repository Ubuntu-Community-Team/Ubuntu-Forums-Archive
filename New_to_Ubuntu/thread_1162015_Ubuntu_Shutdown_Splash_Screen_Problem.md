---
title: "Ubuntu Shutdown Splash Screen Problem?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-17
When i shutdown UBUNTU the splash screen image looks like a negative image,But the startup splash screen image is perfect How to repair it

---

### Post by mprince on 2009-05-17
One thing you could take a look at is this file:

```
sudo gedit /etc/usplash.conf
```

Make sure it matches your monitor's resolution.

```
# Usplash configuration file
xres=1280
yres=1024
```

---

### Post by ravi_buz on 2009-05-17
Yes the resolution is correct but the image is like a photo of ubuntu in xray or negative or some thing like that

---

### Post by ravi_buz on 2009-05-18
Any help ???????

---

### Post by redman5087 on 2010-02-21
have the same problem, it does only occur with the 64 bit , I think

---

