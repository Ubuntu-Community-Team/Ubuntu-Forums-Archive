---
title: "I'm new to ATI video cards.  How do I find out what version driver I'm using?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by diablo75 on 2009-04-21
I just got a new laptop today and it has (according to lspci):

ATI Technologies Inc RS690M [Radeon X1200 Series]

There isn't anything shown in my Hardware Drivers manager for any video card drivers.  Desktop effects seemed to be enabled by default after installing the system and they run almost perfect (there is occasional flickering).

So I'm wondering if there might be some better drivers available that I don't know about.  Thanks!

---

### Post by steve101101 on 2009-04-21
under hardware drivers you can see if any proprietary ones are being used. you can also enable new ones here aswell.

---

### Post by diablo75 on 2009-04-21
As I mentioned in the OP, there are no drivers (at least not for a video card) shown in Hardware Drivers...

---

### Post by steve101101 on 2009-04-22
try is command

fglrxinfo

---

### Post by diablo75 on 2009-04-22
> **steve101101 said:**
> try is command

fglrxinfo

It required installing xorg-driver-fglrx but I got it in.  After typing the command, it gave me:

```
david@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4

```

---

### Post by steve101101 on 2009-04-22
it seems like it doesn't know about your video card b/c its not using the proprietary drivers. However if its working okay you don't need to use them unless you want to. 

This page, [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide), may help you install the drivers. I have never used an ATI card as I always buy NVidia. you may also be able to directly download .deb from their website.

---

### Post by Yashiro on 2009-04-22
Don't use the 'fglrx' driver. Keep using the open soure ati driver that you're currently running.

---

### Post by diablo75 on 2009-04-22
> **Yashiro said:**
> Don't use the 'fglrx' driver. Keep using the open soure ati driver that you're currently running.

It's kinda buggy but I'll take your word for it... however I would like to know where I can read about the development of this driver so I can keep track of developments.  Perhaps there's a newer version of this driver available as well.  Where can I find information about this driver?

---

