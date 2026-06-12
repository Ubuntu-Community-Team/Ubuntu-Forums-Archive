---
title: "No sound Ubuntu 9.10"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by ChaimaaMer on 2010-04-18
Hello,

I hv just installed ubuntu 9.10 inside my windows XP , but neither the headphones, nor the speakers are working ... I am new to this, and I would appreciate your help.

Here is the output of  # lspci -v 

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e9300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

and here is the output of # sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by drascus on 2010-04-18
try in terminal
```
alsamixer
```

that will give you a little graphical representation of your audio levels make sure nothing is muted maybe play with the levels a bit and see if that solves your problem. I have never used Wubi (which from your response I gather your using) but try to boot a live CD and see if you get audio with that. If you do it's probably something specific to Wubi. 

This may also be linked to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271519)

I don't see a bug report for 9.10 for the same card but some of the suggestions and discussions there might be useful.

---

### Post by ChaimaaMer on 2010-04-18
Yes, I am using Wubi . 

I tried the Alsamixer before, unmuted everything , but I have three items that I can't control their volume (they don't have that column that shows their volume) : 

headphones, IEC958, IEC958 Default PCM

---

### Post by lidex on 2010-04-18
Can you post the output of these commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

Also have a look at this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by ChaimaaMer on 2010-04-18
Here they are :-

# uname -a

Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

# aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.20.

# head -n 1 proc/asound/card*/codec#*

Codec: Realtek ALC889A

---

### Post by garvinrick4 on 2010-04-18
HDA intel this always works in my installs of 9.10 just follow instructions then REBOOT.



[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by ChaimaaMer on 2010-04-18
@ garvinrick4

I checked the link , and I am blocked at step 5 , I am getting the error mentioned, and even when I try to launch it manually , I am having this in the terminal

E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


I tried the command " speaker-test " , and I am only getting noise coming out from the speaker.

---

### Post by ChaimaaMer on 2010-04-18
Hi again,

I just rebooted. I managed to open the Volume Control , and  I now have sound coming out from my speakers  :KS

However my headphones are still dead :confused:

---

### Post by lidex on 2010-04-18
What is the make and model of your PC/Laptop?

---

### Post by garvinrick4 on 2010-04-18
This removes and installs a new set of packages from repositories not you own cache of packages. Incase you got a bad one. Cannot hurt give a try if nothing else has worked as
you mentioned. Copy and paste one at a time in terminal

sudo apt-get remove --purge alsa-base 

sudo apt-get remove --purge pulseaudio

sudo apt-get clean && sudo apt-get autoremove 

sudo apt-get install alsa-base 

sudo apt-get install pulseaudio

---

### Post by garvinrick4 on 2010-04-18
> **ChaimaaMer said:**
> @ garvinrick4

I checked the link , and I am blocked at step 5 , I am getting the error mentioned, and even when I try to launch it manually , I am having this in the terminal

E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


I tried the command " speaker-test " , and I am only getting noise coming out from the speaker.this in terminal Code:

[COLOR=Blue]pulseaudio & pavucontrol[/COLOR]

might give an error but should open.

---

### Post by garvinrick4 on 2010-04-18
this should open alsa mixer Code:

 alsamixer [COLOR=Blue]-Dhw[/COLOR]

---

### Post by ChaimaaMer on 2010-04-19
I changed something on the mixer I hv on the windows, and now, the headphones are working on Ubuntu ... my guess that something was wrong with Front Panel settings.

Thanks to everyone :KS

---

### Post by garvinrick4 on 2010-04-20
> **ChaimaaMer said:**
> I changed something on the mixer I hv on the windows, and now, the headphones are working on Ubuntu ... my guess that something was wrong with Front Panel settings.

Thanks to everyone :KS Your settings in Windows have nothing at all to do with your sound in Ubuntu it is something you did in Ubuntu than rebooted. To bad you cannot

remember what you did, might have helped others. Have a nice day.

---

### Post by ChaimaaMer on 2010-04-21
@ garvinrick4  

Sorry for the late reply , work !! :(

I am sure you are right , because I discovered that the headphones wasn't even working in windows (They used to !! , I swear :) )

So , When I changed some settings on the mixer in Windows, plugged the head phones in the front Panel , it worked.

Then I rebooted , and logged on to Ubuntu to find the headphones are working,

So, My guess is that its your link which helped, because that was the last thing I did on Ubuntu before rebooting  [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I remember I was blocked in step number 5 , and I rebooted out of despair, and after that the speakers worked but the Head Phones didn't (but seems like it wasn't working anyway like described above)

Sorry if I am confusing everyone :confused:, I am a bit new to this

---

