---
title: "speeding up internet when using mobile broadband"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by anupsg on 2009-12-01
hiiiii i used to use windows n i newly shifted to ubuntu 9.10, when i connected my phone it got auto configured but its really slow. in windows i used to dialup *99# n then get connection which is much faster.
n synaptic packager is not properly integrating with the connection its speed is in bits per second..
N media codecs is not being identified it indefied in my frnz pc plz help

---

### Post by ukripper on 2009-12-01
post output of ```
lsmod 
```and ```
lsusb
```




Below command should install your required codecs.:
```
sudo aptitude install ubuntu-restricted-extras
```

---

