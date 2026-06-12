---
title: "Ati radeon xpress 1100 driver for ubuntu 9.04?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by yoshiki2 on 2009-10-11
I guess i need the driver.. because i can watch movies normaly under xp, but under ubuntu the quality is terrible..

---

### Post by sandyd on 2009-10-11
open a terminal
(applications -> Accessories -> Terminal)
and type in
```

jockey-gtk

```

---

### Post by 3rdalbum on 2009-10-11
You are already running the only driver that is available for that ATI chipset.

ATI does not support the Xpress 1100 on Linux anymore, unfortunately, so you're stuck with open-source support.

In your video playing software, you could try changing the "video output module"; this may improve your playback performance.

---

### Post by yoshiki2 on 2009-10-11
wow ... ........  what for is that code? 
jockey-gtk

---

### Post by sandyd on 2009-10-11
> **yoshiki2 said:**
> wow ... ........  what for is that code? 
jockey-gtk
opens the hardware driver thingy
as 3d album said above, ati doesn't support your card anymore.

p.s. you can try installing the open source driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by suseno on 2009-11-18
Anyone use **xorg-driver-fglrx** driver? I tried to use that on my ATi Radeon Xpress 1100 in Acer Aspire 5050 laptop, Installed from repository. But it didn't work producing messy blank screen.

I remove it using recovery mode (root mode) then

---

### Post by yoshiki2 on 2009-11-23
some1 told me these are the instruction to make the driver work:

Open up a terminal and run the following commands

sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://[anongit.freedesktop.org/xorg/driver/xf86-video-ati]("http://anongit.freedesktop.org/xorg/driver/xf86-video-ati")

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install

But now.. when I try to dl the file, it just cannot find it.. [anongit.freedesktop.org/xorg/driver/xf86-video-ati]("http://anongit.freedesktop.org/xorg/driver/xf86-video-ati")

or was I making a mistake trying to install this driver? How can i know i've not messed up my driver's configuration?

---

### Post by Mark Phelps on 2009-11-24
> **yoshiki2 said:**
> How can i know i've not messed up my driver's configuration?

There is no ATI driver that works with current Ubuntu versions and your card ... period.  No matter how you try to install one.

Carlee provided a link that has instructions for removing ATI drivers and replacing them with open source drivers.  Follow those instructions and you will get video back.

---

### Post by Dinoyc on 2009-12-28
[COLOR=#000000][FONT=Verdana]Hi All,

Even i am facing the same problem with my Acer 5100 series laptop where it has the below configuration

AMD turion 64 mobile technology
MK36 (2.0 Ghz,512k L2 cache)
15.4" widescreen WXGA wide Crystal brite TFT LCD
ATI Radeon Xpress 1100 Graphics Card
60GB PATA HDD
DVD-super Multi doule layer
(support DVD+R Doule Layer /DVD += RW)
512 MB RAM

I have installed Ubuntu 9.10 and i don't see any reason why we need to upgrade to 9.10 and degrade the kernel and XORG if that was the case then it would always be good to work on 8.10. I need to know if ubuntu is working with ATI to give us a legacy driver?
If yes then when is that day coming? is there a way we can mail the technical team of ubuntu to make them understand that issue?

Could someone suggest the best ATI graphics to upgrade to right now? which has a low budget and works in this configuration?[/FONT][/COLOR]

---

### Post by Mark Phelps on 2009-12-29
>  ... I need to know if ubuntu is working with ATI to give us a legacy driver? If yes then when is that day coming?...
ATI is NOT going to provide support for Linux for the "legacy" cards -- they have already made that clear.  If you're waiting for this, you're waiting for something that is not going to happen
> ... is there a way we can mail the technical team of ubuntu to make them understand that issuue?
The open source drivers are constantly being improved.  The folks working them are well aware of the issues.  They will not provide predicted future release dates.

---

