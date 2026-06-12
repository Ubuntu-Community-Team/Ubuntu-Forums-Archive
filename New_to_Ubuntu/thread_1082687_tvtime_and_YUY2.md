---
title: "tvtime and YUY2"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-02-28
I installed tvtime, and I can't get it working.
When I start it, it shuts down immediately.
starting it in terminal it gives me:
```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/darrell/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

lspci states I have the followin vodeocard:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
```

My capture card is a:
```
Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```


According to softpedia, it should have YUY2 support, or at least the latest ati driver should have it. I have installed the proprietary driver through the option ubuntu gives you after first detection.

Why am I still getting this error and is there a way to correct this?

---

