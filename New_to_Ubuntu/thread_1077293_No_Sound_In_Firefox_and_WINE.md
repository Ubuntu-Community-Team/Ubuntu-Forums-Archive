---
title: "No Sound In Firefox and WINE"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by EfrenP on 2009-02-22
Problem:  sound doesn't work in wc3 under wine, or in flash in firefox
I'm using an Logitec USB Headset: [http://www.techshout.com/images/logitech-clearchat-pro-usb-headset-india.jpg](http://www.techshout.com/images/logitech-clearchat-pro-usb-headset-india.jpg)

I changed my settings to work with the headsets, music works fine with VLC and Pidgen.

For WINE I get this error:

```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f658,0x00000000), stub!

```

I don't really know what more info you need but I'm happy to provide it if you ask

---

### Post by llamabr on 2009-02-22
Why are you using wine?  And what program is failing in wine?

Wine is always the last answer, and probably, whatever you're trying to do, can be done just as well without bothering with windows applications.

---

### Post by EfrenP on 2009-02-22
I probably didn't clarify right, I have problem with my audio using wine, and I have another problem with audio on Firefox (with flash) because videos on youtube don't have any audio.

I'm using an USB Headset from Logitec, I don't have speakers so I don't know if its just my headsets or the audio in general.

---

### Post by rlzyoner on 2009-02-22
Reinstall the Adobe Flash .deb package and try now.
That sorted my Firefox audio problem

---

