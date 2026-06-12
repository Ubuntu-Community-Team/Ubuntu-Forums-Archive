---
title: "Can't boot Karmic LiveCD"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Tahakki on 2009-11-07
I downloaded the Karmic image, checked it with MD5. Fine. Then put in in, booted it to the menu, and selected 'Check disc integrity'. Fine.


Then I try to boot from the LiveCD, and when it gets to logging in the screen starts moving and flickering, and eventually goes all white and grey.

Safe graphics mode just gets me a terminal, but I can't type anything as it's flickering too.

Help?!

---

### Post by Ant59 on 2009-11-07
What graphics card do you have. It may not be supported by the open-source drivers on the LiveCD.

---

### Post by Tahakki on 2009-11-07
It's an nVidia card that works perfectly with Jaunty and Hardy - GeForce 4400 Ti.

---

### Post by Ant59 on 2009-11-07
Oh. :s

I think there are a lot of graphics problems that people are having with Karmic, that didn't affect Jaunty. I can't help you because I don't know exactly what's changed, and how to fix it.

EDIT:

You could try the alternate CD, and see if it works after installing.

---

### Post by Bunnybugs on 2009-11-07
Have you tried to boot Jaunty (9.04), and upgrade to Karmic (9.10)??

Had some of the same trouble with Karmic booting

---

### Post by Tahakki on 2009-11-07
> **Bunnybugs said:**
> Have you tried to boot Jaunty (9.04), and upgrade to Karmic (9.10)??

Had some of the same trouble with Karmic booting
Nope. I've had lots of problems with upgrading in the past and don't want to mess up my Jaunty install. I was planning to put Karmic in a separate partition.

---

### Post by Tahakki on 2009-11-07
I've downloaded the image for the alternate CD, but I'm nervous to use it - what package do I need to install to get X to start working? I'm assuming if I install with the text-based thing I won't get any graphics at all, since this crappy driver won't support my card?

---

### Post by Tahakki on 2009-11-07
Okay, burned the alternate installer DVD and installed. Worked fine, until it booted for the first time and I had the same issue as before.

I used Envy to install the right driver, but still nothing.

The following is the whole of xorg.conf from the Karmic install.


```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
EndSection

```

I think it looks suspiciously short? Please, help me?

---

