---
title: "USB Sound Card Driver Help; Creative X-Fi"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by scarrman on 2010-08-25
hi,

i'm trying to get a usb sound card (creative x-fi 5.1 surround) installed.  there is a driver (unsupported) from creative here:

[http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz)

but there's no .configure file; i'm thinking of trying to create a .configure file using the method (autoconf) here:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

however, i'm not sure this is going to be my best approach.  in a nutshell, i'm trying to use it to run mixxx and currently audio is uncontrollable through the usb sound card (extremely loud and lugubrious quality, no volume control), although it works fine through the built-in notebook soundcard.

hardware is dell vostro 1000, amd64; pulseaudio installed (disabled during mixxx, however)

ideas?  especially help on driver compile?  i'd love to be able to use the 5.1 usb card, as it sounds good through my windows computer...

thx! :)

---

### Post by scarrman on 2010-08-26
oops, set the sample rate to 48 khz (and set to analog stereo output in sound preferences) and it fixed the poor audio quality.  it'd still be great to utilize the whole 5.1 sound, but i'm relatively satisfied that i'll be able to gig this weekend. 

i went ahead and tried the autoconf approach, but no luck--seriously not sure what i'm doing...

---

