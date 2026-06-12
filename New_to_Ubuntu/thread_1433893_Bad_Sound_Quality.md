---
title: "Bad Sound Quality"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by martinis on 2010-03-19
Hi! just installed ubuntu 9.10 on my Hp Compaq 8510p laptop and have soundquality problems! 

I get sound ot of the speakers, but it sounds like i'm listening to a radio with bad reception! This aplies to all sounds I play, and the quality drop is severe from before i installed Ubuntu! 

The sound preferences meny have a "hardwhere" tab, where there is 2 options:
Internal Audio 1 output/1 input analog stereo duplex
and
RV630/M76 audio device [Radeon HD 2600 Series] 1 output Digital stereo HDMI output

The first is marked at the moment, and if i mark the other all sounds just disapears! I've got a feeling Im supposed to use the second alterative to get soundquality, but it wont work.

Any ideas on how to solve this?

Thanks in advance! //M

---

### Post by Psumi on 2010-03-19
Try purging pulseaudio:

sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio

Then...

sudo apt-get install alsa-utils gstreamer0.10-x

After that, in terminal, use gstreamer-properties and make sure that Default Output is set to Autodetect.

Reboot and try sound again. After purging Pulseaudio, your gnome-volume applet will not work.

---

### Post by Enigmapond on 2010-03-19
> **Psumi said:**
>  After purging Pulseaudio, your gnome-volume applet will not work.

There are two workarounds for this. Either install gnome-alsamixer and alltray and place the mixer on the panel or install Avant Window Navigator or Docky and add a volume applet to either.

Good Luck!

---

### Post by sandyd on 2010-03-19
just do
```

sudo mkdir /etc/init.d-disabled
sudo mv /etc/init.d/pulseaudio /etc/init.d-disabled
sudo dpkg --purge gstreamer0.10-pulseaudio

```

---

### Post by Psumi on 2010-03-19
> **carlee said:**
> just do
```

sudo mkdir /etc/init.d-disabled
sudo mv /etc/init.d/pulseaudio /etc/init.d-disabled
```

You need to purge gstreamer0.10-pulseaudio for alsa to work in gstreamer programs, sorry.

---

### Post by sandyd on 2010-03-19
> **Psumi said:**
> You need to purge gstreamer0.10-pulseaudio for alsa to work in gstreamer programs, sorry.
done :D

---

### Post by alex1973 on 2010-08-12
Did it work? Thanks.

---

