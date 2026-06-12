---
title: "cannot record audio with recordmydesktop"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-02-13
Hello
I have been trying to fix the no audio problem on my own but failed badly :(

julio@julio-ThinkCentre-M52:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
0a:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
julio@julio-ThinkCentre-M52:~$ 

how do I enable the software to use sound?  Also i downloaded skype and did an audio test call and it recoreded nothing :(

any help 
thx

---

### Post by ikt on 2011-02-13
have you seen?

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by vezolmi on 2011-03-28
This works for me. Taken from [http://flax.ie/ubuntu-10-04-gtk-recordmydesktop-screen-casting/](http://flax.ie/ubuntu-10-04-gtk-recordmydesktop-screen-casting/) :

gtk-recordMyDesktop  (records video + audio) and gnome-sound-recorder (records audio) can  record both the system and the microphone sound. To choose the sound to  be recorded open gnome-volume-control (from ALT+F2 for example), click  on Hardware, then on Profile and there choose the corresponding option,  depending on what will be recorded ..:
+ sound of the system: a) Analog Stereo Output; or b) Digital Stereo Duplex (IEC958)
 + sound from the microphone: a) Analog Stereo Duplex; or b) Digital Stereo (IEC958) Output + Analog Stereo Input
In  gnome-volume-control, it may be necessary to choose “Off”, close it,  open it again, choose the desired option and close it again.
Some  of the other options may work sometimes, but they may record sometimes  the system sound and sometimes the mic sound. And other options may  record audio but could not permit to listen to the recorded sound. So  it’s better not to use those options.
NB: system sound is the  sound of what one can hear from the speaker. It can be a .ogg or .mp3, …  song played by Totem, or a Flash music video of a web site, …

---

### Post by vezolmi on 2011-03-28
No need for Skype at all.

---

### Post by vezolmi on 2011-03-30
I've tried xvidcap and gtk-recordMyDesktop. I've been able with both of them to record video and audio from the system or the microphone.

But gtk-recordMyDesktop has 2 problems:
a) When you click on stop it takes a lot of time to encode the video (in xvidcap you have it in the moment you stop the recording).
b) It uses a lot of space in a folder called more or less /tmp/rMD-session-xxxx. Sometimes is deleted after the encoding but sometimes not (keeps on growing) and you have to delete it before your Linux root partition (/) gets full.

To be able to record the sound with xvidcap you just need to follow a few steps to install it properly:
[http://ubuntuforums.org/showthread.php?t=1714139](http://ubuntuforums.org/showthread.php?t=1714139)

---

