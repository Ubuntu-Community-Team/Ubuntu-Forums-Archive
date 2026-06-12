---
title: "USB Microphone Problem"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Zopiac on 2009-07-14
I have a USB microphone that has worked fine on Ubuntu before, but on this computer, it is having problems. It has always displayed as Logitech USB Microphone in the Sound Preferences, but on this computer it just shows up as USB Input in the Sound Capture box. However, when I have even that selected, I do not get input. In the Device Drop-Down box in Sound Preferences, at the bottom, it lists it fine, but it just doesn't allow me to use it as my Sound Capture device. How do I get this to work?

---

### Post by khelben1979 on 2009-07-14
What is the brand of the USB Microphone? 

If the Linux kernel have inbuilt support for that hardware it will work automatically, as it probably did before. Otherwise you either need to build it as a kernel module or switch to another Linux kernel.

---

### Post by Zopiac on 2009-07-14
> **khelben1979 said:**
> What is the brand of the USB Microphone? 

If the Linux kernel have inbuilt support for that hardware it will work automatically, as it probably did before. Otherwise you either need to build it as a kernel module or switch to another Linux kernel.

It is Logitech, as I stated (but it mght not have been exactly obvious)

What do you mean, about the kernel?

---

### Post by cooper77z on 2009-07-14
dude, I had problems after using a logitech usb mic too! Darnet! I am afraid to use it again, though I might just to prove them to be malicious. It's an hour and a half penalty if I am right or wrong.

---

### Post by khelben1979 on 2009-07-15
> **Zopiac said:**
> It is Logitech, as I stated (but it mght not have been exactly obvious)

The exact model number from Logitech is interesting to know about.

> **Zopiac said:**
> What do you mean, about the kernel?

That you probably need another kernel with better support for your Logitech hardware. Your present kernel supports it, but it may not be using the correct driver for it (I don't know).

---

### Post by Zopiac on 2009-07-15
> **khelben1979 said:**
> The exact model number from Logitech is interesting to know about.

Uhm... Rock Band Microphone? ^_^ It's really all I have on it. It works perfectly fine on my other computers (Ubuntu Studio 9.04 and Windows XP) but not on this one (Ubuntu 8.04). (Technically it doesn't work on my Kubuntu 9.04 computer either, but I can't get sound to fully work on it anyways)

---

### Post by cooper77z on 2009-07-16
My rock band usb mic worked great in 8.04, but I think I messed up my system while I was modifying the way my system used the mic.

---

### Post by Zopiac on 2009-07-28
Bump? I need the mic to work; this is my audio production computer ^_^ and I'm too cheap to get an actual mic.

---

### Post by sandeepraj on 2009-07-28
try updating kernal..
```

sudo apt-get update

```

---

