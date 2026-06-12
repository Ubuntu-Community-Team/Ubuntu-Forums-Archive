---
title: "webcam installation"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by openkt on 2009-05-18
please guide me how to install my webcam on 8.10
my cam is frontech usb cam. i cheese ,camaroma both of them are not workin.
so,apparentlly im not able to do video chat on skype :sad:

---

### Post by candtalan on 2009-05-18
have you tried the skype options settings I wonder?
(at the bottom of the skype window)
there is a video settings  there which might be useful.

---

### Post by s.fox on 2009-05-18
Hi and welcome to the forums.

Can you open up terminal and post the output of this command please:

```
ls usb 
```

Thanks,

-Ash R

---

### Post by canadiandude007 on 2009-05-18
I would find out exactly which type of webcam you are using by:

```
lsusb -l
```

Then look it up here:

[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

Depending on what it says, you might need to compile a module into your system.

---

