---
title: "640x480 only option when connected to TV"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by ischemic on 2010-09-05
Hi,

I've got an Acer Revo running 10.04 than has an nvidia ion chipset. I've connected it to my Panasonic VT20 plasma and the only option I get in the nvidia xserver config panel is 640x480. Does anyone know how I can make it display the full resolution of my TV?

Thanks

---

### Post by redbook4574 on 2010-09-05
how are you connected to the TV ??

---

### Post by ischemic on 2010-09-05
> **redbook4574 said:**
> how are you connected to the TV ??

D-Sub.

---

### Post by cariboo on 2010-09-05
Have you run:

```
sudo nvidia-xconfig
```

and rebooted?

The above command creates an xorg.conf that should help with your resolution problem.

---

### Post by ischemic on 2010-09-05
That didn't work.

Would connecting via HDMI help? I've got one spare HDMI socket and a 4th hdmi cable coming from amazon in the next day or so.

---

