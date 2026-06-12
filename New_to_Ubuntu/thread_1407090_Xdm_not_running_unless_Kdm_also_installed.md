---
title: "Xdm not running unless Kdm also installed?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by abben on 2010-02-14
I just installed a bare-bones debian system on a very old computer (98mb ram and I think a 500mghz processor). I started with no graphical interface of any kind. I installed xdm, xinit, and icewm. Freshly installed, I would type xdm in the hopes of seeing a login screen, and it would run, but never leave text mode. I would try startx, but it returned an error...

> /etc/X11/xinit/xserverrc: line 5: /usr/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 5: exec /usr/bin/X11/X: cannot execute: No such file or directory
giving up
xinit:  No such file or directory (errno 2): unable to connect to X server
xinit:  No such process (errno 3): Server error

But when I installed kdm, not only did kdm work, **but xdm and startx began working also**.

To install Kdm, I also needed to install a huge list of packages:

```
xserver-xorg menu-xdg libfreebob0 xserver-xorg-video-rendition
  libarts1c2a kdelibs4c2a libartsc0 xserver-xorg-input-evdev
  xserver-xorg-video-s3virge xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark libiec61883-0
  xserver-xorg-video-ati xserver-xorg-video-radeonhd libilmbase6
  xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-glint xserver-xorg-video-fbdev
  xserver-xorg-input-wacom libart-2.0-2 xserver-xorg-video-v4l
  libjack0 xserver-xorg-video-mga kdelibs-data kdebase-data
  kdebase-bin-kde3 xserver-xorg-input-mouse
  xserver-xorg-video-r128 libarts1-akode xserver-xorg-video-nsc
  xserver-xorg-video-openchrome libxslt1.1
  xserver-xorg-video-vesa xserver-xorg-video-siliconmotion
  xserver-xorg-video-mach64 xserver-xorg-video-tga
  xserver-xorg-video-sis xserver-xorg-video-vga
  xserver-xorg-video-s3 xserver-xorg-video-nv xserver-xorg-core
  libfam0 xserver-xorg-video-tseng xkb-data
  xserver-xorg-video-savage libakode2 fam xserver-xorg-input-all
  xfonts-base libavahi-qt3-1 oss-compat kdebase-bin libopenexr6
  xserver-xorg-video-vmware xserver-xorg-input-kbd libsamplerate0
  libjasper1 xserver-xorg-video-i128 xserver-xorg-video-neomagic
  xserver-xorg-video-chips xserver-xorg-video-voodoo
  libgl1-mesa-dri xserver-xorg-video-i740
  xserver-xorg-video-cyrix xserver-xorg-video-dummy x11-xkb-utils
  xserver-xorg-input-synaptics xserver-xorg-video-sisusb
  xserver-xorg-video-imstt xserver-xorg-video-radeon
  xserver-xorg-video-cirrus xserver-xorg-video-intel
```

After I uninstalled kdm, xdm continued to work beautifully, but aptitude told me the above packages were unnecessary and that I should **sudo apt-get autoremove** them. If I autoremoved them, xdm and startx stop functioning. If I reinstall them, xdm and startx function fine.

So I have a few questions:

(1) Did I botch my install of Xdm? All I did was **sudo apt-get install xdm xinit icewm** plus the related dependencies auto-suggested by aptitude. Was I wrong to expect Xdm to work out of the box? 

(2) Is aptititude lying to me? It says I can remove all those xserver-xorg packages. But Xdm works when they are installed. *Can* xdm work without all those xserver-xorg-video packages?

Lastly, I'll note that I haven't touched a single config file of any sort related to xdm or xinit, yet both worked perfectly after kdm was installed.

With your help I'll be able to overcome adversity just like the Sklar brothers, pictured here.

---

### Post by abben on 2010-02-14
> **abben said:**
> Freshly installed, I would type xdm in the hopes of seeing a login screen, and it would run, but never leave text mode. I would try startx,** but it returned an error**.

I feel as though I've left out an important piece of info, so I'm going to go back and reproduce this error message, and post the text. 

In the meantime, I've attached this jpg of comedian Paul F. Tompkins to express my gratitude for any help.

---

### Post by abben on 2010-02-14
I googled my error message, and came up with [one hit]("http://www.oesf.org/forum/index.php?showtopic=25666&st=390&p=177629&#entry177629"):

> I just upgraded packages on my universal, install titchy-phoneui-shiny and apt-get autoremove 
and now I've lost my X server

[B]mojo:~# /etc/X11/xinit/xserverrc: line 5: /usr/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 5: exec: /usr/bin/X11/X: cannot execute: No such file or directory
xinit: Server error.[/B]

Sumuo, I was using your image, which package provided the Xserver?

EDIT:
Never mind;

**# ln -s /etc/X11/X /usr/bin/X11/X**

fixed it

I tried linking the two just like this person did. But I got the same error as before when trying to run xdm. 

Here's a picture of Tim Heidecker.

---

### Post by abben on 2010-02-14
Ok, my mistake was just as dumb as I expected it might be. I was missing the xorg. Why in gods name is that not a mandatory package for anyone installing xdm? (That or one of the kdm tag along packages). 

So if I just did a core system install and then

```
apt-get install xdm xinit xorg [window manager of choice]
```

everything would have been fine.

Enjoy this still of standup comedienne Sabrina Matthews.

---

### Post by gvoima on 2010-02-14
I've usually only installed the core package of X with xdm and it worked fine on a base debian install.
```
apt-get install x-window-system-core
```
Alongside with xmonad as a window manager.

---

### Post by abben on 2010-02-14
> **gvoima said:**
> I've usually only installed the core package of X with xdm and it worked fine on a base debian install.
```
apt-get install x-window-system-core
```
Alongside with xmonad as a window manager.

Yeah, that's exactly what I was missing in fact. I went to install x-window-system-core and it said "installing xorg package instead". But why in gods name is it not a mandatory package? Or at least something that is mentioned on the man page or at least recommended by aptitude? Perhaps there are several alternative packages people might decide to use...

The ravishing Helen Hunt makes an entrance.

---

### Post by NightwishFan on 2010-02-14
If you feel inclined to do so, file a bug on the package.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Here is the immortal lord of voice Christopher Lee. :D

---

