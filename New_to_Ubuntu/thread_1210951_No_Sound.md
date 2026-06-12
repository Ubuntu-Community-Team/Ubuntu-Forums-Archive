---
title: "No Sound"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by TheEvilOne6620 on 2009-07-12
I just installed Ubuntu to my HP DV41275mx and have no sound at all.  I had sound for  aminute through headphones only but whne I tried to apply a fix now I have nothing.  Im a toatl beginner and need help;   Any one have any ideas to this

---

### Post by nhasian on 2009-07-12
please give us more information about your setup.  what version of ubuntu are you using?  have you tried double clicking on the speaker icon and adjusting the volume levels?

can you give us the terminal output of:

```
lshw -C multimedia
```

---

### Post by TheEvilOne6620 on 2009-07-12
Yes I have tried double clicking its turned on.  When I first installed I looked up on the net and did a few things, then my soundcard was showing.  Now when i run from the terminal my card shows up sometimes .  The fix I used most of hosed sometihng.. Any ways Im trying to understand how to install drivers for it I have no idea how.   It seems to say this when I use aplay command: 

  **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device  3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
shane@shane-laptop:~$ 

when I try to download the drivers I get this
laptop:~$ sudo modprobe snd-hmd=intel
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Module snd_hmd=intel not found.
shane@shane-laptop:~$ 


any ideas whats going on herer?

---

### Post by nhasian on 2009-07-12
it would also help if you showed us the page or commands you used when you borked your system ):P

---

### Post by TheEvilOne6620 on 2009-07-12
ook this is what i followed here: to get the previous post::
[LEFT]_**[SIZE=3]General Help - Start here if you have no idea why sound is not playing[/SIZE]**_[/LEFT]
      
[LEFT][SIZE=2]**(1)** Go to a shell and type:  	Code:
 	aplay -l 
[/SIZE][/LEFT]
this displayed my sound card.  Then I tried this:
[SIZE=2]**(4)** Now go back to the shell and type  	Code:
 	sudo modprobe snd-hmd-intel



[/SIZE]and that is how I ran it to try and download the driver but with no luck I also tried doing this as I saw it as a fix on another forum but i get no luck it tells me its not found.

I also tried the different other potential solutions discussed on other threads by editing /etc/modprobe.d/alsa-base.conf and trying different combinations of these lines.
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5




what else do you need to know tell me i will provide it...

---

### Post by nhasian on 2009-07-12
hmm you still didnt mention which version of ubuntu you have.  you can check from a terminal with

```
lsb_release
```

also to get your sound working try:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by TheEvilOne6620 on 2009-07-12
I also have tried this and cant tell if its even recognizing my card.
Open a terminal window, and type "lspci -v | less".  This will check your computer's motherboard, and attempt to list out all devices that it's recognized as installed. 

when i run the aboce command this is all i get:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
        Subsystem: Hewlett-Packard Company Device 30fb
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: d2300000-d24fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00006fff
        Memory behind bridge: d1300000-d22fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
:
???????

---

### Post by TheEvilOne6620 on 2009-07-12
I am using the newest version of ubuntu 9.04 x64bit on a AMD processor

---

### Post by nhasian on 2009-07-12
> **TheEvilOne6620 said:**
> I am using the newest version of ubuntu 9.04 x64bit on a AMD processor

If you have an AMD CPU and sigmatel STAC92XX audio chipset, why are you trying to use intel audio drivers? hehe

you dont need lspci.  only:

```
lshw -C multimedia
```

---

### Post by TheEvilOne6620 on 2009-07-12
This is what I get when running the command you just provided:

  *-multimedia            
       description: Audio device
       product: RS780 Azalia controller
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

when I browse through the Matrix for alsa drivers none of the ATI drivers correspong to this ????

---

### Post by nhasian on 2009-07-12
see if this is helpful:


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

edit /etc/modprobe.d/alsa-base

add at the end of the file:

```
options snd-hda-intel model=laptop
```

reboot

---

### Post by duanedesign on 2009-07-12
In System/Administration/Users and Groups , make sure that your user and the root user are members of the following groups:

 pulse
 pulse-access
 pulse-rt

Then try this procedure:

**1.** copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

**2.** and add these lines to the end of the file:

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

**3.** Then navigate to System>Preferences>Sound and change everything to ALSA

**4.** reboot and retest sound

**5.** If sound still does not work, then replace hp-dv5 with one of the following 4 model options:

 STAC92HD71B*
   ref
   dell-m4-1
   dell-m4-2
   dell-m4-3

**6.** You will have to reboot and retest sound after every model option change to the alsa-base.conf file
---------------------------------------------------------------
Also check sound levels. In Terminal

```
alsamixer
```

and make sure none of them are set to 0

-
-

---

### Post by duanedesign on 2009-07-12
This Question on Launchpad describes your exact problem sound only in headphones using your card. The above procedure is the first solution that seemed to work for the person who posted the problem. However there are additional links and info in case this does not work.

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/72235](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/72235)

---

