---
title: "No sound in Kubuntu 10.04"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by fairy._.queen on 2010-07-12
Hi all!
I have Kubuntu 10.04 installed on my laptop and the sound doesnt work at all (e.g. no sound on youtube videos). In another thread it was suggest to install GNOME ALSA mixer to solve the problem, but as i dont think i can install it on a KDE environment, could you please suggest me something else that might work?
Thanks in advance!

---

### Post by fairy._.queen on 2010-07-12
tags added, sorry for forgetting.

---

### Post by sandyd on 2010-07-12
> **fairy._.queen said:**
> Hi all!
I have Kubuntu 10.04 installed on my laptop and the sound doesnt work at all (e.g. no sound on youtube videos). In another thread it was suggest to install GNOME ALSA mixer to solve the problem, but as i dont think i can install it on a KDE environment, could you please suggest me something else that might work?
Thanks in advance!

alright.
Try these steps 

a) Press ALT+F2, and type in "konsole"
In the black box that opens, type in 
```
alsamixer
```
check that nothing is muted, or set at a low volume.

b) Press Control + C
type in 
```

aplay -l
```
and post the output to the forum

c) Type in
```

lspci
```
and also post the output.

---

### Post by fairy._.queen on 2010-07-13
Thnx so much Carlee!
now, as for point a), i did unmute the mute items, but couldnt raise the volume of S/PDIF (which, incidentally, i dont know what is :-P).
Heres the output of aplay -l
```
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 3: INTEL HDMI [INTEL HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
Heres the output of lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0d:06.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 01)
0d:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0d:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)

```

Thank you so much!

---

### Post by sandyd on 2010-07-15
if your using pulseaudio, try installing pavucontrol, and at the last tab, disable the HDMI output. in the "output" tab, disable everything other than the soundcard your using. make sure the card is not muted there, as alsamixer wont show if pulseaudio is muted or not.

---

### Post by fairy._.queen on 2010-07-15
Sorry to ask such a question, but how do i know whether im using pulseaudio or not?:oops::oops::oops:

---

### Post by fairy._.queen on 2010-07-19
Maybe my question was indeed stupid, but i am a beginner and im eager to learn.
how do i know if im using pulseaudio?

---

### Post by sandyd on 2010-07-19
> **fairy._.queen said:**
> Maybe my question was indeed stupid, but i am a beginner and im eager to learn.
how do i know if im using pulseaudio?
eh. your question wasnt stupid.
I was busy dealing with my new daughter for the last week or so (me losing track of time...)

if your using pulseaudio, 
running
```

pulseaudio
```
should give output

if it gives "command not found", its not installed.

Pulseaudio/ALSA is currently a bit weird on the KDE side.
KDE has awesome pulseaudio support, and it just works out of the box, but it isn't the default (alsa is). Applications such as Amarok decide to access the sound card directly when pulseaudio is not installed, causing other apps not to be able to use it.

so if its not installed, try
```

sudo apt-get install pulseaudio
```

---

### Post by fairy._.queen on 2010-07-20
:-* :-* :-*
i installed pulseaudio + pavucontrol and it worked!!!!!!
thanks so much, sound is important to me!

Congrats on your daughter, to whom i dedicate this piece:
[http://www.youtube.com/watch?v=v0CLYpYKHNY&NR=1](http://www.youtube.com/watch?v=v0CLYpYKHNY&NR=1)

THANKS! :-({|=\\:D/:guitar:=D>

---

