---
title: "Dell E1505 plays audio but with wrong drivers in  ubuntu 10.10"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by hadrons123 on 2010-10-23
Hi I am a newbie to ubuntu....My dell E1505 has sigmatel 92xx audio card(in windows 7) but the installed drivers shown here in ubuntu is intel HD audio.


dragon@littlehangleton:~$ uname -a
Linux littlehangleton 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
dragon@littlehangleton:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dragon@littlehangleton:~$ dpkg -l | grep "alsa"
ii  alsa-base                                          1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                                         1.0.23-2ubuntu3                                   Utilities for configuring and using ALSA
ii  bluez-alsa                                         4.69-0ubuntu2                                     Bluetooth audio support
ii  gnome-alsamixer                                    0.9.7~cvs.20060916.ds.1-2                         ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                 0.10.30-2                                         GStreamer plugin for ALSA


The problem is it plays audio and records voice through the mic ,but the sound recording is very choppy and with lot of noise in the background.The audio playing through the speakers are choppy too.I think i dont know how to select the sigmatel device.I kinda guess the sigmatel 92xx audio drivers are installed.I read in some forums that I would be able to choose the hardware device from sound preferences icon.but i cant see the sigmatel device in sound preferences too...Need help please....

---

