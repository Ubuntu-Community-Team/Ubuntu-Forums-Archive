---
title: "Lucid Lynx sound plays through headphones and speakers... tried other methods, help!"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by shiftylock on 2010-06-12
I have an HP G60 laptop running lucid lynx, and every time I plug headphones into my laptop the sound plays through the headphones and speakers. I have tried some methods (using alsamixer, etc.) but with no results. I'm fairly new to Ubuntu, so I'm sorry if this is a noobish question.

---

### Post by SRST Technologies on 2010-06-12
What have you tried?

---

### Post by shiftylock on 2010-06-12
[http://ubuntuforums.org/showthread.php?p=9402208#post9402208](http://ubuntuforums.org/showthread.php?p=9402208#post9402208)
and using alsamixer, but there is no "front" option for me...

---

### Post by terry_gardener on 2010-06-12
my sisters laptop had this problem recently but with 9.10and the way i sorted it was by deleting the /home/username/.pulse folder and reboot and then it worked normally.

---

### Post by shiftylock on 2010-06-12
> **terry_gardener said:**
> my sisters laptop had this problem recently but with 9.10and the way i sorted it was by deleting the /home/username/.pulse folder and reboot and then it worked normally.
Nope... still plays through headphones and speakers... if it helps I have a Conexant 5067 audio driver I think...

---

### Post by fordguydude on 2010-06-12
I'm having the same problem. Apparently we have to wait for some ASLA drivers to be released?

---

### Post by CaronMargarete on 2010-06-13
> **fordguydude said:**
> I'm having the same problem. Apparently we have to wait for some ASLA drivers to be released?

Fordguydude, where did you get that info? 

I have the same problem.
[http://ubuntuforums.org/showthread.php?p=9453564#post9453564](http://ubuntuforums.org/showthread.php?p=9453564#post9453564)

---

### Post by shiftylock on 2010-06-13
Actually, I remember reading a bug report about a possible update being released. Not sure which one... Anybody have any suggestions?

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by shiftylock on 2010-06-14
```
Linux chad-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
Codec: Conexant ID 5067


```Does this help? I have an HP G60 laptop. Thank you in advance!

---

### Post by lidex on 2010-06-15
You sound like a candidate for linuxant. Go here to download the conexant alsa driver deb. Install and reboot.[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by shiftylock on 2010-06-15
You deserve a nobel prize or something! Wow! My sound now switches flawlessly from my headphones to my speakers. Many thanks :)

---

### Post by CaronMargarete on 2010-06-18
Wondering if I should do this too???

> **lidex said:**
> You sound like a candidate for linuxant. Go here to download the conexant alsa driver deb. Install and reboot.[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

> **lidex said:**
> Can you post the output of these terminal commands  for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*  
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

```
 caz@Jamie:~$ uname -a
Linux Jamie 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
caz@Jamie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
caz@Jamie:~$ dpkg -l | grep "alsa"
ii  alsa-base                                       1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                        1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                      1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                      4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                              0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                    0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                            1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
caz@Jamie:~$ head -n 1 /proc/asound/card*/codec#* 
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
caz@Jamie:~$ 

```Thoughts? 
Note: My problems may be more extensive than just sound simultaneous through headphones and speakers, see: [http://ubuntuforums.org/showthread.php?t=1508545](http://ubuntuforums.org/showthread.php?t=1508545)

---

### Post by sahayes on 2010-07-26
Lidex, thank you for posting this fix.  I am certainly not complaining, since it seems to have worked, but when I checked under ALSA Mixer, it called the sound chip Conexant CX20583 (Pebble 56-LQFP).  Can that be changed back to Conexant 5067, or is that even possible? It's okay if it isn't.

Thanks,
Scott

---

### Post by lidex on 2010-07-26
> **sahayes said:**
> Lidex, thank you for posting this fix.  I am certainly not complaining, since it seems to have worked, but when I checked under ALSA Mixer, it called the sound chip Conexant CX20583 (Pebble 56-LQFP).  Can that be changed back to Conexant 5067, or is that even possible? It's okay if it isn't.

Thanks,
Scott
The linuxant driver is from conexant, so i don't know what to tell you. It may have been incorrectly identified before, which could have been the problem. If it works I wouldn't mess with it.

---

### Post by sahayes on 2010-07-26
Sounds good.  I was also wondering if this package will work with future versions of the linux kernel and ALSA drivers?  Sorry but I'm still pretty new to Linux.

---

### Post by lidex on 2010-07-26
> **sahayes said:**
> Sounds good.  I was also wondering if this package will work with future versions of the linux kernel and ALSA drivers?  Sorry but I'm still pretty new to Linux.
Hopefully newer versions of alsa will support that codec out-of-the-box. If not, it would depend on conexant providing updates.

---

