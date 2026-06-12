---
title: "Trying to fix poor ATI video drivers and their problems"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Xeoncross on 2009-01-29
Ok, I have a Core2Quad (x64) with 4GB DDR2 1066, and a 512MB ATI Radeon HD 3780 Video Card. So you would think that with this much power I could handle any type of media requirements.

Anyway, I want to know if anyone knows of some good resources on ATI Drivers.

I used the ones that are suggested by Ubuntu (don't know what version I think I might have read 8.3 somewhere) and they only allow me to view simple stuff like still images ok.

But with any kind of videos everything starts de-syncing and slowing down. Thanks to [the VLC fix]("http://sarp.erdag.org/index.php/2008/12/solved-video-flickering-on-ubuntu-810-with-ati-graphics-card-using-compiz/") I got VLC able to play videos without flickering like crazy. But even the player scruber lags like the video is too much for the player or something.

Also, when using recordMydesktop the whole system slows to a crawl (and the video that I record is choppy) and when I start istanbul it takes like 25% of my CPU just to run it (and as soon as it starts it stops responding).

Anyway, all these problems tell me that I need to get the RIGHT video card drivers. So I went to ATI's site and downloaded the 8.12 drivers and did a auto install - nothing changed. So then I followed [some of the recommend steps]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") (before I found that guide) and when I re-started the screen went blank when Ubuntu loaded. So I had to boot in safemode and fix X-window (I think it pulled a backup or something) and then login and delete all the ATI stuff I could find - reboot and finally install the offcial Ubnutu ATI drivers again.

Now I am back to square one. I have spent a lot of time on this and I am not afraid to do hard stuff to get this to work. If I can't use any media related stuff (like videos or screen recording) then Ubuntu is of no use to me.

---

### Post by sandyd on 2009-01-29
type this in the terminal

```

sudo apt-get install envyng-core envyng-gtk
sudo envyng -t

```

choose the drivers that is both compatible and recommended.

---

### Post by Xeoncross on 2009-01-29
Thanks, but I appear to already have that one.
```

+---------------------------------------------------------------------------+
 | Number | Candidate Version | Installed Version | Compatible | Recommended |
 |---------------------------------------------------------------------------|
 | 0      | 8.552-0ubuntu0.1  | 8.552-0ubuntu0.1  | +          | +           |
 +---------------------------------------------------------------------------+


```

---

### Post by Meelis on 2009-02-19
Hi

Linux screencasting software doesn't support fast hardware. There aint no multicore support ad ****. Most times you even are not able to launch other software simultaneously with screencasting. Software like Xvidcap 1.1.7 Istanbul 0.2.2 recordMyDesktop	0.3.8.1 are **soooooo OLD**.

Under windows you can convert DVD 720x576 to huffyuv wth 1 core 400fps. Same time with other core to screencast it 30fps @1680x1050. It's no problem to browse web same time.

Linux will froze even 1-5fps @1440x900 (firefox will open after 3min).

[http://www.youtube.com/watch?v=cJg40Ad03sk]("http://www.youtube.com/watch?v=cJg40Ad03sk")

---

### Post by jml75 on 2009-02-26
Hi!

The latest drivers from ATI, version 9.2, are much better then the ones that are distributed with 8.10.

Here is how to install then :

1 - Download the drivers
```

mkdir latest-fglrx
cd latest-fglrx/
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run

```
2 - Make the downloaded file executable
```

chmod +x ati-driver-installer-9.2-x86.x86_64.run

```
3 - Run the downloaded file to generate the packages for Ubuntu 8.10
```

./ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/8.10

```
4 - Install the generated packages
```

sudo dpkg -i fglrx-amdcccle_8.582-0ubuntu1_i386.deb fglrx-kernel-source_8.582-0ubuntu1_i386.deb fglrx-modaliases_8.582-0ubuntu1_i386.deb libamdxvba1_8.582-0ubuntu1_i386.deb xorg-driver-fglrx_8.582-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.582-0ubuntu1_i386.deb

```
5 - Reboot your computer to apply the changes

That's all! You should be up and running after that and you should motice a substential improuvement in performance.

As for your flickering problem when you playback video, you simply have to change your "/etc/X11/xorg.conf" file so the "Device" section looks like this :

```

Section "Device"
    Identifier     "Device0"
    Driver         "fglrx"
    VendorName     "AMD/ATI"
    BoardName      "Radeon HD 3780"
    Option         "OpenGLOverlay" "false"
    Option         "VideoOverlay"  "true"
EndSection

```

And then reboot your computer or simply restart X windows by pressing CTRL+ALT+BACKSPACE.

Cheers!

---

### Post by ender1598 on 2009-02-26
Thanks!  These instructions are exactly what I needed too!

---

### Post by Meelis on 2009-02-28
Hi

Should i uninstall old ATI driver (8.54.3), (OpenGL 2.1.8087) before installing 9.2? If yes then how?.

Does new driver fixes poor recordMyDesktop performance?

---

### Post by zeroemissions on 2009-03-01
> **Meelis said:**
> Hi

Should i uninstall old ATI driver (8.54.3), (OpenGL 2.1.8087) before installing 9.2? If yes then how?.

Does new driver fixes poor recordMyDesktop performance?

I think to uninstall video drivers you use

```
sudo sh fglrx-uninstall.sh
```

---

### Post by jml75 on 2009-03-03
No you don't have to uninstall them first.

Since the installer generates .DEB packages, it should only be a metter of upgrade and dpkg -i will do it automatically for you.

So if you follow the instructions, you should not worry about your old drivers, they will be uninstalled in the upgrade process taken care of by dpkg.

cheers!

---

### Post by jml75 on 2009-03-03
As for the poor recordMyDesktop performances, they do not.

As far as I know, to get decent performances from this desktop recording app with an ATI card, you need to disable desktop effects.

Cheers!

---

### Post by saul11 on 2009-03-07
I tried the steps described by jml75, becuase I think it might be the reason ahy I can't boot into Ubuntu8.10 which I installed with Wubi, see my post about it [here]("http://ubuntuforums.org/showthread.php?p=6855831"). But when I tried 'wget [https://a248.e.akamai.net/f/674/9206...x86.x86_64.run](https://a248.e.akamai.net/f/674/9206...x86.x86_64.run)' I got 'unable to resolve host address "a248.e.akamai.net"' :(

I also tried editing the xorg.conf, but it has almost nothing in it (only identifier under section 'device')!? Tried adding the Driver and VendorName, but I didn't have permission to save the file...

Is there something else I can try?

---

### Post by Meelis on 2009-03-10
I installed Ati driver 9.2 and yes no performance improvements for recordMyDesktop.
1 CPU core is allways 100% and other software is unresponsive. When i close RMD then every app starts and works.

Can someone tell what is wrong with Ati?

---

### Post by matteojg on 2009-03-10
I have an ATI driver as well, and if I have visual effects enabled I am unable to play most videos.

Try setting Visual Effects to none (System>Preferences>Appearance>Visual Effects).

---

### Post by Meelis on 2009-03-10
My visual effects are off.
[Video captured @ 1024x576 10fps]("http://www.youtube.com/watch?v=cJg40Ad03sk")

[Fullscreen it's soo mutch worse]("http://www.youtube.com/watch?v=t3O2HoMYSjA")

---

