---
title: "Mobile GM965/GL960 Integrated Graphics Controller problem"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by deepbluedna on 2009-03-19
Hi, I am really exhausted already with my video card.
I was trying to install a autodock tool on my ubuntu 8.10,32bit. My laptop is Thinkpad T61 and the video card is "Mobile GM965/GL960 Integrated Graphics Controller". Everytime I tried to run the autodock tool there is error says "TclError: Togl: couldn't get visual". I cannot find any help on the autodock website. So I figured maybe I should get a better driver for my video card. I have installed the compizconfig manager but it doesn't seem give me any help. I have the cube effect now so I figured it is not the hardware's problem. Is anyone here can give me any help on this problem? Thanks a lot.

---

### Post by solitaire on 2009-03-19
Have you tried these drivers?

[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)

or if you're feeling very crazy there's the unstable versions of the drivers:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

*READ THE PAGE* before installing either set of drivers.

---

### Post by deepbluedna on 2009-03-19
I tried to install the nvidia glx 96 pakcages with synaptic package manager.
Then I lost my cube effect, but the error in running autodock tools changed to "TclError: Togl: X server has no OpenGL GLX extension". No idea. HELP!!!

---

### Post by solitaire on 2009-03-19
"Mobile GM965/GL960 Integrated Graphics Controller"
This is an "INTEL" chipset not Nvidia!

The Nvidia drivers will not work.
Use the first link in my post into your software sources and install them.

---

### Post by D3ath on 2009-03-19
> **solitaire said:**
> "Mobile GM965/GL960 Integrated Graphics Controller"
This is an "INTEL" chipset not Nvidia!

The Nvidia drivers will not work.
Use the first link in my post into your software sources and install them.
Please do what this guy said that is how you get your drivers back!

---

### Post by deepbluedna on 2009-03-19
I failed in installing those packages, there is an error says "dependency is not satisfiable: libdrm2". I also tried to install those packages with synaptic package manager, I installed the  "libdrm-dev" "libdrm2" "xserver_xorg-video-intel", but it still doesn't work. Any help?

---

### Post by deepbluedna on 2009-03-20
any other help here?

---

### Post by kalana on 2009-04-27
Maybe this will help
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

