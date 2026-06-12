---
title: "webcam surveillance"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by chmbrs on 2009-02-22
hello forum.

 im looking for a simple webcam motion detector app. i heard of zoneminder but its too advanced for me. i just need something really simple, motion sensor webcam surveillance app. simple to use, low cpu usage would be great plus. 

also an app to turn off a wireless card completely. or a way to do it thru the terminal?

Thanks in advance.

---

### Post by sandyd on 2009-02-22
```

sudo ifdown wlan0

```
to turn off wifi card maybe?

---

### Post by chmbrs on 2009-02-22
i messed with it a little bit. i tried a couple commands but the card is still working and detecting networks. i kind of got it under control with network selector app
thanks for quick reply.

how about a webcam, motion detector surveillance software for linux thats pretty simple.

---

### Post by conradcliff on 2009-04-06
I'm also looking for a surveillance utility for my webcam. I found one but it was like 9 years old and didn't even want to try it.

---

### Post by mxboy15u on 2009-04-22
I have been using a windows one that works great and auto-uploads to my FTP. Sad that Linux does not offer anything of substance in this arena.

---

### Post by suitedaces on 2009-04-22
This any use to you? [http://www.zoneminder.com/](http://www.zoneminder.com/)

---

### Post by egalvan on 2009-04-22
> **chmbrs said:**
> hello forum.

 im looking for a simple webcam motion detector app... i just need something really simple, motion sensor webcam surveillance app. simple to use, low cpu usage would be great plus. 
Thanks in advance.

Under Synaptic,

"motion"

size: 807kb
download:269kb

here is the "description"

[I]V4L capture program supporting motion detection
Motion is a program that monitors the video signal from
one or more cameras and is able to detect if a significant
part of the picture has changed. Or in other words, it can
detect motion.

Motion is a command line based tool. It has no graphical
user interface. Everything is setup either via the
command line or via configuration files.

The output from motion can be:
   - jpg files
   - ppm format files
   - mpeg video sequences

Also, motion has its own minimalistic web server. Thus,
you can access the webcam output from motion via a browser.[/I]

---

### Post by Godly on 2009-04-22
Thanks, Egalvan! Good stuff.

---

### Post by conradcliff on 2009-04-22
zoneminder looks pretty sweet, I think I'm going to try that one out.

---

