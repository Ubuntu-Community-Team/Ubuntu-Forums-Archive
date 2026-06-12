---
title: "How should Cheese work?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by krgottschall on 2010-02-09
Recently installed Karmic Koala. Cheese was not part of the install so I added it using Synaptic Package Manager. I can capture photos and vidios, so it seems to be working OK, but ...

My question is: Should the main screen show a MOVING image of what of the camera sees?   When Cheese starts, the webcam takes a still photo and shows that until I restart Cheese.  I don't know what a photo or video will look like until after it has been taken and I view the result.  Don't know if this helps but the webcam light is on the whole time Cheese is running.

If the screen SHOULD show a moving image, how do I make that happen?  

Thanks, Ken

---

### Post by patchwork on 2010-02-09
Cheese shows a moving image on my 9.10, and places the stills below the video frame.  I don't see any obvious settings that would allow you to change the behavior you're seeing.

---

### Post by krgottschall on 2010-02-10
Patchwork,
 
Exactly how did you install Cheese?  i.e. *sudo apt-get install cheese.*  Also what, if any, libraries, packages, etc.; did you install to help cheese?
 
Thanks, Ken

---

### Post by patchwork on 2010-02-10
I used apt-get, and any libraries needed were automatically installed.

If you think you may have dependency problems, you can try this

```
cd /usr/bin
ldd cheese           ## will show status of dependencies
```Look for anything that says 'Not found'

My dependencies are as follows:

```
kevin@crystalpepsi:/usr/bin$ ldd cheese
    linux-vdso.so.1 =>  (0x00007fff4abd4000)
    libgnome-desktop-2.so.11 => /usr/lib/libgnome-desktop-2.so.11 (0x00007f672ffc7000)
    libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f672f9bc000)
    libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0x00007f672f7b2000)
    libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f672f506000)
    libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f672f2e6000)
    libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f672f0bd000)
    libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f672ee38000)
    libz.so.1 => /lib/libz.so.1 (0x00007f672ec21000)
    libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f672e9ef000)
    libgstreamer-0.10.so.0 => /usr/lib/libgstreamer-0.10.so.0 (0x00007f672e71b000)
    libebook-1.2.so.9 => /usr/lib/libebook-1.2.so.9 (0x00007f672e4df000)
    libedataserver-1.2.so.11 => /usr/lib/libedataserver-1.2.so.11 (0x00007f672e2b4000)
    libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00007f672df66000)
    libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0x00007f672dd29000)
    libsoup-2.4.so.1 => /usr/lib/libsoup-2.4.so.1 (0x00007f672dada000)
    libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0x00007f672d865000)
    libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f672d5bb000)
    libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0x00007f672d3a0000)
    libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0x00007f672d132000)
    libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00007f672cf2d000)
    libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0x00007f672cd0b000)
    libhal.so.1 => /usr/lib/libhal.so.1 (0x00007f672cafa000)
    libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00007f672c8bb000)
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007f672c69f000)
    librt.so.1 => /lib/librt.so.1 (0x00007f672c497000)
    libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f672c28b000)
    libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f672c042000)
    librsvg-2.so.2 => /usr/lib/librsvg-2.so.2 (0x00007f672be0b000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f672bbef000)
    libm.so.6 => /lib/libm.so.6 (0x00007f672b96b000)
    libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f672b6e8000)
    libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f672b4a1000)
    libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f672b29d000)
    libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00007f672afd6000)
    libgstinterfaces-0.10.so.0 => /usr/lib/libgstinterfaces-0.10.so.0 (0x00007f672adc4000)
    libc.so.6 => /lib/libc.so.6 (0x00007f672aa55000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f672a71f000)
    libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f672a516000)
    libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f672a313000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f672a111000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f6729f0b000)
    libxcb-aux.so.0 => /usr/lib/libxcb-aux.so.0 (0x00007f6729d07000)
    libxcb-event.so.1 => /usr/lib/libxcb-event.so.1 (0x00007f6729b02000)
    libxcb-atom.so.1 => /usr/lib/libxcb-atom.so.1 (0x00007f67298fd000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f67296e1000)
    libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f67294d8000)
    libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f67292bd000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f67290ab000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f6728ea1000)
    libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f6728c9f000)
    libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f6728a94000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f672888a000)
    libexpat.so.1 => /lib/libexpat.so.1 (0x00007f6728661000)
    libdl.so.2 => /lib/libdl.so.2 (0x00007f672845d000)
    libcamel-1.2.so.14 => /usr/lib/libcamel-1.2.so.14 (0x00007f67281e0000)
    libnss3.so => /usr/lib/libnss3.so (0x00007f6727eac000)
    libnssutil3.so => /usr/lib/libnssutil3.so (0x00007f6727c8e000)
    libsmime3.so => /usr/lib/libsmime3.so (0x00007f6727a63000)
    libssl3.so => /usr/lib/libssl3.so (0x00007f672782e000)
    libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00007f67275a6000)
    libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x00007f67272ee000)
    libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00007f67270c3000)
    libcom_err.so.2 => /lib/libcom_err.so.2 (0x00007f6726ebf000)
    libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00007f6726c91000)
    libplds4.so => /usr/lib/libplds4.so (0x00007f6726a8d000)
    libplc4.so => /usr/lib/libplc4.so (0x00007f6726888000)
    libnspr4.so => /usr/lib/libnspr4.so (0x00007f672664d000)
    libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x00007f67263ab000)
    libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x00007f672619a000)
    libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x00007f6725f22000)
    libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0x00007f6725d1b000)
    libpcre.so.3 => /lib/libpcre.so.3 (0x00007f6725aed000)
    libresolv.so.2 => /lib/libresolv.so.2 (0x00007f67258d4000)
    libselinux.so.1 => /lib/libselinux.so.1 (0x00007f67256b6000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f67301ef000)
    libgsf-1.so.114 => /usr/lib/libgsf-1.so.114 (0x00007f6725477000)
    libcroco-0.6.so.3 => /usr/lib/libcroco-0.6.so.3 (0x00007f672523e000)
    libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f6724ff9000)
    libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00007f6724d6e000)
    libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00007f6724b64000)
    libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00007f6724949000)
    libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f6724722000)
    libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f672451e000)
    libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f6724315000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f6724112000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f6723f0d000)
    libuuid.so.1 => /lib/libuuid.so.1 (0x00007f6723d08000)
    libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x00007f6723b00000)
    libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00007f67238fd000)
    libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x00007f67236f9000)
    libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007f67234e8000)

```

My gut feeling is that it isn't a dependency problem, but rather a compatibility issue...but I may be wrong

---

### Post by Jefferythewind on 2010-02-10
Yeah Cheese seems to work pretty normally for me.  The pciture moves until you take a snap shot, and then it appears in the bar below.

---

### Post by krgottschall on 2010-02-10
I ran the *ldd cheese* command and got ALMOST the same list of dependencies that you posted.  None of them showed as  "Not Found".  I did get 2 differences from your list. They are:
linux-vdso.so.1 -- yours
linux-gate.so.1 -- mine
/lib64/ld-linux-x86-64.so.2 -- yours
/lib/ld-linux.so.2 -- mine

I am guessing these are due to you running the 64 bit version and me running the 32 bit version. 

Do you have any ideas what incompatibilities might cause my problem if the above differences are not the problem?

Ken

---

### Post by patchwork on 2010-02-10
I'm not really sure.  What is the make and model of your webcam?  Do you have the program hwinfo installed?  If you do, can you output the result of 

```
hwinfo |grep -i cam
```

This will list all applicable hardware (if your camera has the string "cam" or "Cam" anywhere in its name.  For example:

```
kevin@crystalpepsi:~$ hwinfo |grep -i cam
  input.product = 'BisonCam, NB Pro'
  info.product = 'BisonCam, NB Pro'
  info.product = 'BisonCam, NB Pro'
  usb.interface.description = 'BisonCam, NB Pro'
  usb_device.product = 'BisonCam, NB Pro'
  info.product = 'BisonCam, NB Pro'
  access_control.type = 'camera'
  <6>[   17.279083] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0300)
  <6>[   17.361664] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input7
    product = "BisonCam, NB Pro"
    product = "BisonCam, NB Pro"
  N: Name="BisonCam, NB Pro"
bus = 3, name = BisonCam, NB Pro
  E: ID_MODEL=BisonCam__NB_Pro
  E: ID_MODEL_ENC=BisonCam\x2c\x20NB\x20Pro
  E: ID_SERIAL=5986_BisonCam__NB_Pro
  E: NAME="BisonCam, NB Pro"
  S: input/by-id/usb-5986_BisonCam__NB_Pro-event-if00
  E: ID_MODEL=BisonCam__NB_Pro
  E: ID_MODEL_ENC=BisonCam\x2c\x20NB\x20Pro
  E: ID_SERIAL=5986_BisonCam__NB_Pro
  E: DEVLINKS=/dev/char/13:71 /dev/input/by-id/usb-5986_BisonCam__NB_Pro-event-if00 /dev/input/by-path/pci-0000:00:1d.7-usb-0:6:1.0-event
  S: v4l/by-id/usb-5986_BisonCam__NB_Pro-video-index0
  E: ID_V4L_PRODUCT=BisonCam, NB Pro
  E: ID_MODEL=BisonCam__NB_Pro
  E: ID_MODEL_ENC=BisonCam\x2c\x20NB\x20Pro
  E: ID_SERIAL=5986_BisonCam__NB_Pro
  E: DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-5986_BisonCam__NB_Pro-video-index0 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:6:1.0-video-index0
  links: /dev/char/13:71, /dev/input/by-id/usb-5986_BisonCam__NB_Pro-event-if00, /dev/input/by-path/pci-0000:00:1d.7-usb-0:6:1.0-event
  links: /dev/char/81:0, /dev/v4l/by-id/usb-5986_BisonCam__NB_Pro-video-index0, /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:6:1.0-video-index0
  Model: "BisonCam, NB Pro"
  Device: usb 0x0300 "BisonCam, NB Pro"
  Device Files: /dev/input/event7, /dev/char/13:71, /dev/input/by-id/usb-5986_BisonCam__NB_Pro-event-if00, /dev/input/by-path/pci-0000:00:1d.7-usb-0:6:1.0-event

```

---

### Post by krgottschall on 2010-02-10
I had to install *hwinfo* then tried Cheese again.  There was no change.  The webcam I have is a Logitech Webcam C250.  I don't know where the reference to "UVC" comes from.

Here is my output of the *hwinfo |grep -i cam* command.

```
ken@ken-desktop:~$ hwinfo |grep -i cam
  input.product = 'UVC Camera (046d:0804)'
  info.product = 'UVC Camera (046d:0804)'
  info.product = 'UVC Camera (046d:0804)'
  access_control.type = 'camera'
  <6>[   12.437068] input: UVC Camera (046d:0804) as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input5
  N: Name="UVC Camera (046d:0804)"
bus = 3, name = UVC Camera (046d:0804)
  E: NAME="UVC Camera (046d:0804)"
  E: ID_V4L_PRODUCT=UVC Camera (046d:0804)
  E: SOUND_FORM_FACTOR=webcam
  prop read: vayM.f3p4oHCaMnF (failed)
  old prop read: vayM.f3p4oHCaMnF (failed)
  Unique ID: vayM.f3p4oHCaMnF
  Parent ID: vayM.f3p4oHCaMnF
```I see a couple of items failed above.  Does that mean  I need a better driver for my webcam?  If so, is there an *apt-get* command to install the right driver for my camera?

I hope I am not becoming a pest but I do appreciate your help.

Ken

---

### Post by patchwork on 2010-02-10
UVC means USB Video Class.   

Support for some Logitech devices in linux is spotty, though it looks like there is some hope.

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04681.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04681.html)

I am still digging into this, but have not yet found anything conclusive one way or the other

EDIT:  Many other Ubuntu users have posted in the forums that their c250's are working correctly out of the box.  Did you have to do anything special to install this camera?

---

### Post by patchwork on 2010-02-10
This may be worth a try.  Your camera is listed as being supported.

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by no2498 on 2010-02-10
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2

this comes from inside cheese's help file faq's

---

