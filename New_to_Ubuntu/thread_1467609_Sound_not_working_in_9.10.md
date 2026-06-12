---
title: "Sound not working in 9.10"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by xPreatorianx on 2010-04-30
Hello everyone, I've just recently switched over to ubuntu. I have been using it for about 2 months and had this machine setup as a cheap server. Well I was gonna use my old gaming machine since I upgraded again. But i need a power supply. 

Anyways, I decided to reinstall ubuntu 9.10 on this machine again. Well for some reason I don't have any sound at all. Everything is unmuted but I still can't get audio. It was like that on 9.04 I believe and now 9.10. I've reformatted and reinstalled about 5 times. I'm running out of ideas and I need a computer to work on until my parts come back for my new machine(rma.)

But this system is extremely old. It's only got 512MB of ram an old AGP Nvidia card. 1 core Processor. and a onboard sound card.

This is what is listed with aplay -l 

```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Any help would be appreciated. I'm trying to get sound working so I can watch some movies and talk on TS until my stuff get's back from RMA. I am also trying to setup TS3 again on this machine for my clan. But I can't do any of that when I can't hear anything.

---

### Post by Sealbhach on 2010-04-30
Hi, have a look at this thread, from someone with the same sound device:

[http://ubuntuforums.org/showthread.php?t=1349803](http://ubuntuforums.org/showthread.php?t=1349803)

Also, it's useful to try the sound troubleshooting procedure, to pin down exactly what the problem is:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

.

---

### Post by xPreatorianx on 2010-05-01
I fixed it, I just used my front panel connectors on my case instead of the back ports.

---

