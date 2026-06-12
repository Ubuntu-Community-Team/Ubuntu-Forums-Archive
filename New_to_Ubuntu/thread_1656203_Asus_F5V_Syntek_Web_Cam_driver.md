---
title: "Asus F5V Syntek Web Cam driver"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by bangkoka on 2010-12-30
Hi,
I installed ubuntu 10.10 on my laptop for the first time but it seems that I'm not able to get my webcam to work. It's a built-in webcam and lsusb says:
```

Bus 003 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 059b:0370 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I followed this _[tutorial]("http://doc.ubuntu-fr.org/syntek")_ but I got stuck on this part:
```

sudo modprobe stk11xx

```with this error:
```

FATAL: Error inserting stk11xx (/lib/modules/2.6.35-24-generic/kernel/drivers/usb/media/stk11xx.ko): Invalid argument

```I tried installing both the 1.4 and 2.0 driver with no luck.
It doesn't work on cheese or skype, and with gstreamer-properties I get the following output when trying v4l and v4l2 on the Video Default Input:
```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]

```Also dmesg output is:
```

[  681.426011] stk11xx: disagrees about version of symbol video_devdata
[  681.426025] stk11xx: Unknown symbol video_devdata (err -22)
[  681.427625] stk11xx: disagrees about version of symbol video_unregister_device
[  681.427632] stk11xx: Unknown symbol video_unregister_device (err -22)
[  681.428249] stk11xx: disagrees about version of symbol video_device_alloc
[  681.428257] stk11xx: Unknown symbol video_device_alloc (err -22)
[  681.428941] stk11xx: disagrees about version of symbol video_register_device
[  681.428949] stk11xx: Unknown symbol video_register_device (err -22)
[  681.429860] stk11xx: disagrees about version of symbol video_device_release
[  681.429868] stk11xx: Unknown symbol video_device_release (err -22)

```Do any of you know what is going on here? Thank you.

---

### Post by nnamdi on 2010-12-30
ok what you have to o is to install cheese it works fine with most webcam i have seen... so if you want to install it you either do it via synaptics or terminal

```


sudo apt-get install cheese


```

run that command on your terminal it would install cheese then after installation type cheese on your terminal or look for it under application.

---

### Post by bangkoka on 2010-12-30
Thank you for your quick response, but as I said before I already tried it on cheese and skype and it doesn't work. 
I don't have /dev/video0 so I assume it must be lack of a proper driver?

---

### Post by Merlinpilot on 2011-02-27
Try this - it worked for me - 10.10 on Asus FS3e:

[U][http://gylling-software.dk/drupal-6.15/?q=node/19](http://gylling-software.dk/drupal-6.15/?q=node/19)

[/U]

---

### Post by Merlinpilot on 2011-02-27
Still have a problem with Skype - shows a black screen although the green camera light is on.   If you open a Terminal and run Skype as super user (sudo skype) then everything works, but I don't know why?

---

