---
title: "No sound in Ubuntu 8.10"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by rootk1t on 2009-01-10
Hi, i've got a Asus F6V-3P195 laptop:

Intel Montevina Core2 Duo P8400 - ATI Mobility Radeon HD3470 256MB VRAM - 4G DDRII667 RAM - 320G SATA HDD - DVD/RW SuperMulti Dual Layer - 802.11a/g/n WLAN - 1.3M Pixel Webcam - BlueTooth - Fingerprint - TPM - 6 Cell - ASUS Bag/Mouse - EXPRESS GATE

with a soundcard:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]


but I have no sound in Kubuntu 8.10 :(

What shoud I do?

---

### Post by rootk1t on 2009-01-11
Anyone? :(

---

### Post by arochester on 2009-01-11
Try [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0) and page down to question #6

---

### Post by mkvnmtr on 2009-01-11
The first thing I would do is go to sound in system preferences and siee if it is turned on.

---

### Post by rootk1t on 2009-01-12
> **mkvnmtr said:**
> The first thing I would do is go to sound in system preferences and siee if it is turned on.

Been there, tried all the sounds, didn't heard a thing.

---

### Post by rootk1t on 2009-01-12
> **arochester said:**
> Try [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0) and page down to question #6

None of those helped me. :confused:

---

### Post by cabralhenrique on 2009-04-12
Hey guys

I'm also using an Asus F6v and I WAS struggling with the no-sound problem for one week. I think the problem is that the sound chip isn't supported by ALSA (it's not listed here [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)). I tried all suggestions I could find online and in the end, what worked for me was to remove both ALSA and PulseAudio and install OSS (just follow the instructions here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound))

Also, to get skype to work properly I had to isntall a skype-static-oss version (available here: [http://packages.medibuntu.org/intrep...tatic-oss.html](http://packages.medibuntu.org/intrep...tatic-oss.html)) and play around with the sound properties until I had the microphone working (in Options in Volume Control, select <front> for the jack-int speaker mode and <input> for jack int-mic mode.

Hope this works for you too!

Cheers,
Henrique

---

### Post by cabralhenrique on 2009-04-13
Turns out that OSS has one major backdraw. it only allows one application using sound at the same time. otherwise, it will give an error...
I uninstalled OSS and went back to my ALSA attempts and now I have everything working as it should. But I had to install the latest versions of alsa packages (nto the same ones that show up in synaptics...).
if you want to try this, just go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and download all the packages on the right hand side. untar them and browse to the folder directory and do:
./configure
make
sudo make install 
make clean
and that's it. restart and voila: sound

h

---

### Post by skalter on 2009-05-09
My recurring problems with sound on Ubuntu are only matched by my recurring problems with keeping ATI video cards working.  In any case, the following has some chance of solving a "just static" issue with very very little pain:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392/comments/12](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275392/comments/12)

To sum up, go to a shell window.  You don't need to sudo for this, just as yourself:

  alsamixer -Dhw

This is an ancient looking terminal interface that may take a few minutes to get used to.  You should be able to do everything with your arrow keys.  If the PCM column is set to 0%, set it to 100% and hit escape.  If you are lucky, your sound will begin to work again.  Unfortunately, like so many "fixes" out there, this is just more voodoo.  I haven't seen an explanation of how a system goes from being in a working state to this state or how to prevent it happening again in the future.

Good luck,

-sdk

---

