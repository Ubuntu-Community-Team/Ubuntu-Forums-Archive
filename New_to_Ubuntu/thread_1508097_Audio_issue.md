---
title: "Audio issue"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by SaaS on 2010-06-12
Hello, I'm Sasse and I'm having some problems. I started using Ubuntu a few days ago and haven't get everything to work as wished yet.

When I play sound in Rhythmbox or VLC it don't sound like it should, I think it could have to do with the Audio Drivers.

I have an integrated Audio card in my ASUS M3A78 Motherboard. On the CD-disc there is a directory named "LinuxDrivers" and in that directory there is three sub-directories named "Audio", "LAN" and "SLED". In "Audio" I got a directory "alsa-1.0.17rc3" and in that directory there are five files listed below.
      alsa-driver-1.0.17rc3.tar.bz2
      alsa-lib-1.0.16.tar.bz2
      alsa-utils-1.0.16.tar.bz2
      install.sh
      readme

The "readme" file goes
```
This Source Code is from www.alsa-project.org!
You can get more infomations about the alsa project from www.alsa-project.org.

Preparation:

Check you have installed below packages:
make            you can type "make --version" to check
gcc             you can type "gcc --version" to check
kernel source   

If you haven't installed these packages, please install them from the distribution CD.

Installation:

1. Automatic install:

./install.sh

Please make sure you are using the GNU shell -- bash to install this script
If you can't install this shell script, you can try "chmod u+x install.sh" to get the permission.

The sound may be muted by default, please type "alsamixer" to change the volume.
```I have tried that but get the error "Second, please make sure you have installed the kernel source. You haven't installed the kernel source."

So I went to the "SLED" directory and found three files "32bit_dd.ahci.img.bz2", "64bit_dd_ahci.img.bz2" and "Readme.txt". The "Readme.txt" goes as follows:
```
It is the driver disk of SB700 for SUSE10(kernel2.6.16.46-0.12). 
install instruction: 
(1) Copy the *.bz2 file to a linux system. 
(2) Use ¡°bunzip2 *.bz2¡± to unzip the file. It should generate a *.img file. 
(3) Plug in a usb flash disk and make sure it is not mounted automatically. 
Check it by command ¡°mount¡±, there is no ¡°sdb related item exists. ( note:  
I suppose the ¡°usb flash disk¡± to be ¡°sdb¡±, if not, please change to the  
right device name) 
(4) Use ¡° dd if=*.img of=/dev/sdb¡± to make a driver disk. 
(5) Start installing OS by pressing F3 and pressing F5 to choose "Driver-Yes" 
(6) Choose "sdb" to update the sata driver
```And I don't understand a thing. :p I have unziped the .img-file for 64bit but nothing more. I don't have an usb flash disc, just a regular usb-memory(or what it is called in English).

Output of "lspci -v" of the "Audio device"
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8345
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Output of "aplay -l"
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


What is "Kernel source" ?
How should I do to install the things in the .img-file?
What will happened after installing the "kernel source" ?

Do you think that it is something else that makes the sound from my  speakers sound bad? In Windows XP it sounds like it should but here in  Ubuntu it sounds hissy.

//Sasse

---

### Post by sandyd on 2010-06-12
What I reallly don't understand is why developers don't simply add their drivers to ALSA in the first place instead of making their own patched versions of ALSA and distributing it, which make it a PITA to use.

anyways...
```

sudo apt-get install linux-source build-essential
```

---

### Post by SaaS on 2010-06-12
I run the [FONT=monospace]"[/FONT]sudo apt-get install linux-source build-essential" code, without knowing what it does really but I'm still getting the error "You haven't installed the kernel source.".

---

### Post by cuberts on 2010-06-12
> **SaaS said:**
> I run the [FONT=monospace]"[/FONT]sudo apt-get install linux-source build-essential" code, without knowing what it does really but I'm still getting the error "You haven't installed the kernel source.".I will need some more information in order to help you. 
First can you type in ```
alsamixer
```into the terminal, (applications>accesories>terminal)
and please paste everything that appears on here.

So I am thinking that the problem is that there is something like Master which is muted.
Another reason why the audio is not working might be because the speakers are not pluged into the right port. That was a problem that I also had, because it was plugged into the Digital Port, which Ubuntu does not recognize.

---

### Post by SaaS on 2010-06-12
Everything? :O

There is pretty much information in here. What is it that you wanna know? Information about the volume on each different output?(Surround, Center, Side, Front, Front Mi, PCM, Headphone)

Tell me more about exactly what you wanna know. =)

/Sasse

---

### Post by SaaS on 2010-06-13
The sound is all fine now, it came right from nowhere. I used Windows XP yesterday because I wanted the sound not to be static hizzy and everything works fine there. But in Windows XP I've installed drivers for my Audio card but in Ubuntu I hasn't. The only thing that makes the sound come to my ears are from the things that Ubuntu have installed automatically on installation.

Like I said, it sounds just fine now but what about tomorrow. I might come back.

I have another thing that's not good thought. In VLC Media Player if I set the volume till more than 100% it get very hizzy just like before but now it's just there. In Windows XP I'm used to set the volume in VLC to 250% but here I can't do that, maybe that depends on the same thing as my previous problem.

Sorry for my bad English. :) I'm learning. :p

How can I check if my Audio card have the correct and latest drivers?

---

