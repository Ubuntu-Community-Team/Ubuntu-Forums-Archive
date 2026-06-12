---
title: "no audio playing cd's..."
date: 2009-07-25
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-25
i can see the seconds going by and know that the cd is playing but have no audio...

i also have no audio when watching you tube videos...

any way to trouble shoot ???

thanks...

---

### Post by NOTAGEEK on 2009-07-25
> **NOTAGEEK said:**
> i can see the seconds going by and know that the cd is playing but have no audio...

i also have no audio when watching you tube videos...

any way to trouble shoot ???

thanks...


i found this fix--- moderngeek.com/node/10 --- but dont understand how to do most of what it suggests...

but got this far

apt-get -y install gnome-volume-control-pulse gnome-alsamixer alsa-oss ubuntu-restricted-extras vlc-plugin-pulse libsdl1.2debian-all asoundconf-gtk xmms2-plugin-pulse padevchooser
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by halitech on 2009-07-25
you need to run the command as sudo
```
 sudo apt-get -y install gnome-volume-control-pulse gnome-alsamixer alsa-oss ubuntu-restricted-extras vlc-plugin-pulse libsdl1.2debian-all asoundconf-gtk xmms2-plugin-pulse padevchooser
```

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> you need to run the command as sudo
```
 sudo apt-get -y install gnome-volume-control-pulse gnome-alsamixer alsa-oss ubuntu-restricted-extras vlc-plugin-pulse libsdl1.2debian-all asoundconf-gtk xmms2-plugin-pulse padevchooser
```

wow---it went ballistic when the sudo was added...

i have no clue what this stuff means...

sudo apt-get -y install gnome-volume-control-pulse gnome-alsamixer alsa-oss ubuntu-restricted-extras vlc-plugin-pulse libsdl1.2debian-all asoundconf-gtk xmms2-plugin-pulse padevchooser
[sudo] password for topsecret: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
ubuntu-restricted-extras is already the newest version.
padevchooser is already the newest version.
The following extra packages will be installed:
  xmms2-core
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  alsa-oss asoundconf-gtk gnome-volume-control-pulse libsdl1.2debian-all
  vlc-plugin-pulse xmms2-core xmms2-plugin-pulse
0 upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 1228kB of archives.
After this operation, 2044kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe alsa-oss 1.0.17-1 [54.2kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe asoundconf-gtk 1.6-0ubuntu1 [6444B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe gnome-volume-control-pulse 2.26.0-0ubuntu3 [72.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libsdl1.2debian-all 1.2.13-4ubuntu3 [221kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse vlc-plugin-pulse 0.9.9a-2ubuntu1 [6890B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe xmms2-core 0.5DrLecter-2ubuntu3 [851kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe xmms2-plugin-pulse 0.5DrLecter-2ubuntu3 [16.3kB]
Fetched 1228kB in 26s (45.5kB/s)                                               
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu3) | libsdl1.2debian-all (= 1.2.13-4ubuntu3) | libsdl1.2debian-esd (= 1.2.13-4ubuntu3) | libsdl1.2debian-oss (= 1.2.13-4ubuntu3) | libsdl1.2debian-nas (= 1.2.13-4ubuntu3) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu3); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 121499 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package alsa-oss.
(Reading database ... 121491 files and directories currently installed.)
Unpacking alsa-oss (from .../alsa-oss_1.0.17-1_i386.deb) ...
Selecting previously deselected package asoundconf-gtk.
Unpacking asoundconf-gtk (from .../asoundconf-gtk_1.6-0ubuntu1_all.deb) ...
Selecting previously deselected package gnome-volume-control-pulse.
Unpacking gnome-volume-control-pulse (from .../gnome-volume-control-pulse_2.26.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libsdl1.2debian-all.
Unpacking libsdl1.2debian-all (from .../libsdl1.2debian-all_1.2.13-4ubuntu3_i386.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_0.9.9a-2ubuntu1_i386.deb) ...
Selecting previously deselected package xmms2-core.
Unpacking xmms2-core (from .../xmms2-core_0.5DrLecter-2ubuntu3_i386.deb) ...
Selecting previously deselected package xmms2-plugin-pulse.
Unpacking xmms2-plugin-pulse (from .../xmms2-plugin-pulse_0.5DrLecter-2ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up alsa-oss (1.0.17-1) ...

Setting up asoundconf-gtk (1.6-0ubuntu1) ...
Setting up gnome-volume-control-pulse (2.26.0-0ubuntu3) ...
Setting up libsdl1.2debian-all (1.2.13-4ubuntu3) ...

Setting up vlc-plugin-pulse (0.9.9a-2ubuntu1) ...
Setting up xmms2-core (0.5DrLecter-2ubuntu3) ...
Setting up xmms2-plugin-pulse (0.5DrLecter-2ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by halitech on 2009-07-25
basically you needed sudo rights to install and once you added sudo, it just went through checking and installing the apps you requested.

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> basically you needed sudo rights to install and once you added sudo, it just went through checking and installing the apps you requested.


thanks---thats a good thing huh ???

oh well i still dont have audio though...

thanks...

---

### Post by halitech on 2009-07-25
what sound card do you have? post the output of
```
lspci
```
```
aplay -l
```
```
lshw -C sound
```

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> what sound card do you have? post the output of
```
lspci
``````
aplay -l
``````
lshw -C sound
```


lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
@DESKTOP:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
@DESKTOP:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by halitech on 2009-07-25
looks like the hardware is being detected fine. try running alsamixer in the terminal and make sure nothing is muted

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> looks like the hardware is being detected fine. try running alsamixer in the terminal and make sure nothing is muted



Card: HDA Intel                                                              &#9474;
&#9474; Chip: VIA VIA VT1708B 8-Ch                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master Front [dB gain=14.00, 14.00] 


pcm looked empty (mute?) ???

---

### Post by halitech on 2009-07-25
usually if its muted it will have MM under it. Try using the right arrow to move over to PCM and press the up arrow to raise the volume and see if you have sound now

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> usually if its muted it will have MM under it. Try using the right arrow to move over to PCM and press the up arrow to raise the volume and see if you have sound now


got pcm un muted now have audio in rhythmbox but it keeps buffering then plays/buffers and i have audio nowhere else... this is becoming a mess...

---

### Post by halitech on 2009-07-25
are you still playing from a cd? have you tried playing an mp3 from the local hard drive?

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> are you still playing from a cd? have you tried playing an mp3 from the local hard drive?
i put a cd in and it wont even start playing in rhythmbox...  as for mp3 i dont know how to play that...

---

### Post by halitech on 2009-07-25
I don't use rhythmbox so not sure .... you would need an mp3 on the computer to try it

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> I don't use rhythmbox so not sure .... you would need an mp3 on the computer to try it


i dont know how halitech but now i tried a cd in rhythmbox again and i have audio !!!

i am ecstatic !!!

thank you soooo much for hangin with me to get this going... u r da man !!!

i am now confident that i will have audio on you tube too...

thread solved... thanks...

---

### Post by halitech on 2009-07-25
glad to hear you got it working. hopefully the audio will work on youtube as well for you, if not you might need to install flash.

---

### Post by NOTAGEEK on 2009-07-25
> **halitech said:**
> glad to hear you got it working. hopefully the audio will work on youtube as well for you, if not you might need to install flash.

ok---thx...

---

### Post by LookTJ on 2009-07-25
open volume control(located at top right corner) then look for pcm. PCM must be up and not muted.

Hope this helps :)

Edit: got here a little late :(

Glad you got it working though :)

---

