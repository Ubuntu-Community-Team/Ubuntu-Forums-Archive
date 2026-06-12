---
title: "LYNX one sound card with ubuntu and Ardour?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by steven lawton on 2011-08-17
hello

I want to install a lynx one sound card with ubuntu 11.04 and ardour 2.8.x.
I am completely new to linux and have done so much fumbling i had to re-install os again! can somebody tell me or send a link as What the following instructions from open sound 4front tech means or what i should do to install their driver oss-linux 4.2-2005_i386.deb
:
warning Linux 2.6 kernel with kernel sources (or kernel headers), GCC Compiler, Binutils,
GNU Make, GTK/GLIB 2.0 libraries must be installed before you can install OSS. Please consult
your Linux distributor’s manuals on how to install and prepare the kernel sources so that external
drivers and modules can be compiled for your kernel.

do i have to make adjustments to my operating system in order to install the correct driver

---

### Post by pi.boy.travis on 2011-08-17
You probably won't have to install a special driver for the sound card. Just hook it up and see if it's recognized. If it isn't we'll go from there.

---

### Post by steven lawton on 2011-08-18
my device will not list under system sounds and i dont know how to install driver 
there is a warning from oss i would like to troubleshoot this first

 "warning Linux 2.6 kernel with kernel sources (or kernel headers), GCC Compiler, Binutils,
GNU Make, GTK/GLIB 2.0 libraries must be installed before you can install OSS. Please consult
your Linux distributor&#8217;s manuals on how to install and prepare the kernel sources so that external
drivers and modules can be compiled for your kernel."

do i have to make adjustments to my operating system in order to install the correct driver

---

### Post by pi.boy.travis on 2011-08-18
Try installing this first:

```
sudo apt-get install build-essential
```

That should give you all the dependencies for building your own modules.

---

### Post by steven lawton on 2011-08-18
Download the driver package from here:     [http://www.4front-tech.com/release/oss-linux-4.2-2005_i386.deb](http://www.4front-tech.com/release/oss-linux-4.2-2005_i386.deb)
    
    type sudo dpkg -i  oss-linux-4.2-2005_i386.deb and then reboot the     machine.
    
    Don't worry OSS will not be shown under the soundcards in Ubuntu. =     Ubuntu only displays ALSA supported devices.
    
    You need to run ossinfo to get the information of the sound devices     in your system. Test out the audio by running osstest command.
    
    best regards
    Dev Mazumdar


the card is installed and working but only online not from my music player and ardour does not see it as a sound card any tips?Im very happy that the first stage is complete i now need to build a daw that is bulletproof
does anyone have any clues?

---

### Post by steven lawton on 2011-08-19
I have a Lynx one audio card it took me three days just to get sound out of it!!!
im am in a similar place when i open Ardour my sound card is not listed and it says no oss drivers are found or alsa drivers how do i configure jackd to show Ardour my system i have sound going in from a audio keyboard and coming out from Internet and the keyboard

almost there im gonna post all my result as i go so that the lynx one user have some more luck its been a battle but im gonna win!!!!!!!!!!!so can anybody tell me how its done!!!

---

### Post by steven lawton on 2011-08-19
brick wall !!!!!

jackd 1 
qoutes
 p, li { white-space: pre-wrap; }  [COLOR=#999999]22:31:09.736 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:31:09.753 Statistics reset.[/COLOR]
 [COLOR=#ff0000]22:31:09.845 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.[/COLOR]
 ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied

---

### Post by steven lawton on 2011-09-09
have installed the oss licensee!!!
now i have sound but only through the INTERNET and from my synthesizer keyboard which is connected to my sound-card(lynx one).

How do i activate my sound from system?..........................................(rhythmbox mp3 player) 

I think i have to use jack 1 to use ardour which i have downloaded in a tar package(how do i install a tar package?)

---

