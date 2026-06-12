---
title: "Totem flicker effect"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Martynwills on 2009-03-14
When I play downloaded flv files (mainly youtube) they download fine but when I play them back although the audio is fine the video flickers the whole way through as if there is a frame rate problem or something. I cannot find any suitable option to correct it in Totem. Any ideas?

Also if I try to pull up a menu by right-clicking it flickers too in a way that means you cannot access anything on it unless you first pause the video playback and the access the menu

I´m running an ATI card if that is any use.

---

### Post by Martynwills on 2009-03-14
I have also found that some flv videos start and the sound begins several seconds after the video so there is a time lag between the two

---

### Post by tripolitan on 2009-03-14
please tell us more about your system (ubuntu version/laptop or desktop/processor/ram/ATI card model etc. Also, do these videos play ok on YouTube? It sounds like a resource problem...

---

### Post by Martynwills on 2009-03-15
I am running ubuntu 8.10 on a laptop.

intel core duo processor T5750 (2.Ghz 667 Mhz 2MB L2 cache)
4Gb DDR2

ATI/AMD proprietary FGLRX graphics driver
ATI Radeon HD 3470 256Mb

The videos play perfectly normally when I view them on You Tube. It is the downloaded flv´s that playback flickering and with sound out of synch with the image.

I have checked my plug-ins on Totem and the youtube one is enabled. I´ve also checked that I have all the extra playback codecs from Gstreamer.

Any ideas anyone?

---

### Post by Martynwills on 2009-03-15
Ie now found that some videos play with sound in synch some do not. Is there any kind of configuration panel? Any suggestions?

---

### Post by fmfrisch on 2009-03-15
Is it only flv's? 

Possible solution would be to disable desktop effects.

---

### Post by Volt9000 on 2009-03-15
Thought I'd throw in my (¢) (¢).

I have the same effect on my laptop, which is running Intrepid Ibex, and also has a Radeon graphics card.

I think this has something to do with the ATI graphics drivers.

---

### Post by fmfrisch on 2009-03-15
yeah im on a ati card too. seems to be a driver related issue. that's why i asked about the desktop effects because disabling those makes all the flicker go away. at least for me.

---

### Post by Martynwills on 2009-03-15
Yep - When I disable desktop effects the video flicker stops.

I am still getting audio out of synch in some cases -

If audio codec in totem is AAC it is out of synch.

If Audio codec is MPEG 2 Audio, Layer 3 (MP3) then it works fine. 

Is there a way for me to change AAC to MPEG in Totem to see if this makes a difference?

---

### Post by Martynwills on 2009-03-15
Is there any solution to the ATI driver issue ?

---

### Post by fmfrisch on 2009-03-15
i've been hitting the forums trying to find a solution and there are a few but nothing works for me.. i just use the compiz-fusion icon to disable desktop-effects temporarly while i watch a video..

---

### Post by WatchingThePain on 2009-03-15
Still movies shouldn't flicker.
My cards ATI and flickers with open gl but not video's even with compiz on. (Radeon 2400 hd)
What about looking at the horiz and vertical refresh rates in
 /etc/xorg.conf?.
Tried other codecs? or a different player like kaffiene or vlc.
Have you got enough ram?.

---

### Post by Martynwills on 2009-03-16
> **fmfrisch said:**
> .. i just use the compiz-fusion icon to disable desktop-effects temporarly while i watch a video..

Sorry to be slow but what is this and where do I find it? :oops:

---

### Post by Martynwills on 2009-03-16
Anyone?

I have the compiz settings manager. I just can find a ¨fusion¨ button I can put up to temporarily suspend graphics settings. I have to do it manually at the momnet to stop the flicker on videos

---

### Post by Martynwills on 2009-03-16
Compiz-fusion icon ..... anyone got any idea?

---

### Post by philinux on 2009-03-16
In synaptic. fusion-icon

or in a terminal 

sudo apt-get install fusion-icon.

I forget where the menu item appears.

[edit] Apps > system tools. I wish people would check the name of apps before posting stuff.

Or in a terminal u can use
metacity --replace
then 
compiz --replace
does a similar thing.

---

