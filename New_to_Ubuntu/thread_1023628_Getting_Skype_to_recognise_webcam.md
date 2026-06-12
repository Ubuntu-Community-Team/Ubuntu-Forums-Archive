---
title: "Getting Skype to recognise webcam"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by CJLees01 on 2008-12-28
I'm having problems getting Skype to pick up the video from my webcam. It's a Dynex 1.3MP USB cam with an integrated mic. I'm using Intrepid and the latest version of Skype freshly downloaded from the repository. 

The weird thing is that the mic works fine on Skype, but the video isn't picked up. Various posts have suggested trying the cam on Cheese and luvcview. The video doesn't work on Cheese (I've read about a bug there on Intrepid), but works fine on luvcview. 

Any ideas or help gratefully received!!

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Relevant bit of dmesg output:

[  948.393047] usbcore: registered new interface driver snd-usb-audio
[  948.572993] uvcvideo: Found UVC 1.00 device Dynex 1.3MP Webcam (19ff:0102)
[  948.583157] input: Dynex 1.3MP Webcam as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input8
[  948.600555] usbcore: registered new interface driver uvcvideo
[  948.603972] USB Video Class driver (v0.1.0)
[  958.043020] 2:3:1: cannot get freq at ep 0x84
[ 1336.195056] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 3320.445403] usbcore: deregistering interface driver uvcvideo
[ 3329.317702] Linux video capture interface: v2.00
[ 3329.359737] uvcvideo: Found UVC 1.00 device Dynex 1.3MP Webcam (19ff:0102)
[ 3329.380267] input: Dynex 1.3MP Webcam as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input9
[ 3329.396543] usbcore: registered new interface driver uvcvideo
[ 3329.398569] USB Video Class driver (v0.1.0)
[ 4165.646291] 2:3:1: cannot get freq at ep 0x84

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

luvcview output:

luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
  Frame size:   640x480
  Frame rate:   15/1 fps (requested frame rate 30 fps is not supported by device)

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

### Post by labinnsw on 2008-12-28
See the first post [here]("http://ubuntuforums.org/showthread.php?t=651375&highlight=Skype+vide"). It should still work on hardy and Intrepid

---

### Post by CJLees01 on 2008-12-28
Thanks but no joy I'm afraid - it is still working fine under luvcview but nothing under Skype.

The post you directed me to looks to be using the gspca driver, but my dmesg log appears to suggest the webcam is picking the uvc driver - could this be anything to do with it?

---

### Post by Dedoimedo on 2008-12-28
Try this, a little old, but might work for you:
[http://ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc](http://ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc)

Dedoimedo

---

### Post by spiderbatdad on 2008-12-28
your cam (19ff:0102) is on this list: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
so it should be working. When you start skype and go to options>>video devices, do you see 'USB 2.0 camera /dev/video0' as in the screenshot below? If the answer is yes, try starting skype with the terminal command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

### Post by CJLees01 on 2008-12-28
Spiderbatdad - you're a genius! Started it from the terminal like you said and it works perfectly.

Thanks a lot.

---

### Post by froggontherocks on 2008-12-28
> **spiderbatdad said:**
> your cam (19ff:0102) is on this list: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
so it should be working. When you start skype and go to options>>video devices, do you see 'USB 2.0 camera /dev/video0' as in the screenshot below? If the answer is yes, try starting skype with the terminal command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

Thank you loading from the terminal works just fine... I wonder why...

---

### Post by KevinGallo on 2009-03-23
The terminal worked for me, but it's not perfect, I get horozontal grey lines going across the image. Any ideas?

---

