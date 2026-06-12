---
title: "NO Sound VIA 82C686A/B - Ubuntu 10.04"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Dark-Space on 2010-07-07
Hi,

I completely new to Linux/Ubuntu.

I just installed Ubuntu 10.04 and I have no sound. I have pretty old notebook (Sharp ) with VIA 82C686A/B sound card on board. Could you help me please to solve the problem. Do I need some drivers?

Regards

---

### Post by warfacegod on 2010-07-07
Not much help other than to say that the VIA video drivers are rather worthless. I imagine that the sound drivers are probably the same.

---

### Post by Dark-Space on 2010-07-07
Thx for reply, I haven't installed any drivers it's just clean Ubuntu install. Do I need install drivers from VIA? I couldn't find any on their website.
Is it mean sound won't work with Ubuntu on my notebook

---

### Post by warfacegod on 2010-07-07
A driver isn't necessarily what you need but I think I found one here: [http://linux-sound.org/drivers.html](http://linux-sound.org/drivers.html)

---

### Post by sandyd on 2010-07-07
hey @warfacegod. you only got 10 more posts until you can change your user tagline! go for it! :)

---

### Post by Dark-Space on 2010-07-07
> **warfacegod said:**
> A driver isn't necessarily what you need but I think I found one here: [http://linux-sound.org/drivers.html](http://linux-sound.org/drivers.html)

Could you tell me how to install it. I downloaded the one below: 
[VIA 82Cxxx Audio  Driver]("http://sourceforge.net/projects/gkernel/") from Jeff Garzik 

I extracted. What command I should use to install it?

---

### Post by warfacegod on 2010-07-07
> **carlee said:**
> hey @warfacegod. you only got 10 more posts until you can change your user tagline! go for it! :)

Shh! We lowly users aren't supposed to know that, but yeah that's why I've been in overdrive for the last few days.

@dark-space. Give me a bit so I can get it myself and read it.

---

### Post by warfacegod on 2010-07-07
> ethtool is a small utility for examining and tuning your ethernet-based
network interface.

This is from the README file. Evidently this isn't an audio driver at all. I have no idea why it was labeled as such in that link I posted.

---

### Post by lidex on 2010-07-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Now have a look at this troubleshooting guide:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by Dark-Space on 2010-07-08
Yes, of course ;)

```
uname -a
Linux Sharp 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: rev40 [VIA 82C686A/B rev40], device 0: VIA 82C686A/B rev40 [VIA 82C686A/B rev40]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
sebastian@Sharp:~$
``````
head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
``````
head -1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC200,200P rev 0

```This is my [COLOR=#000000]recent advance in  technology Sharp PC-GP 1415 ;)

ALSA output: [/COLOR][http://www.alsa-project.org/db/?f=b33a7482669fb7d81dc5a6a62b07afe094a622a0](http://www.alsa-project.org/db/?f=b33a7482669fb7d81dc5a6a62b07afe094a622a0)

I run [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") but still no luck I'm afraid.

[COLOR=#000000]ALSA output after upgrade: [/COLOR][http://www.alsa-project.org/db/?f=a82273af0321db46c7b0b66b2e05a76d0c3e1513](http://www.alsa-project.org/db/?f=a82273af0321db46c7b0b66b2e05a76d0c3e1513)[ ]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by lidex on 2010-07-08
One more please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by Dark-Space on 2010-07-09
Hello,

It's solved now but I'm not sure what helped to fix it. I changed hardware profile in sound preferences.
BTW: yesterday I saw some message that main sound device has changed or something, it was like some device manager but I cannot find it anywhere. Do you know where I can find this option?

Thanks for help.

---

