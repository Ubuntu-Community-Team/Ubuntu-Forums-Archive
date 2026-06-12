---
title: "My laptop is not recognising my headphones"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by neycheva87 on 2011-06-26
Hello everyone. 
Two weeks ago I installed for my first time Ubuntu (I removed my Vista OS and installed Ubuntu 10.10). So the problem was that it was hard to me to make my internal microphone or other microphone working... or working with skype... After trying some different things (like removing pulseaudio - I first tried putting the left channel of the microphone to 100% and the right to 0% to make it mono but this didn't help). After that i removed it and updated ALSA... and now it is working but there is too much noise... but still I can hear with my friends. The problem is that my laptop is not recognising my headphones and that is a problem to me. So here is the info from ALSA: [http://www.alsa-project.org/db/?f=474f87a79af024aeb4d71e1b78149c5f3107f539](http://www.alsa-project.org/db/?f=474f87a79af024aeb4d71e1b78149c5f3107f539).. And I attached the ALSA properties.. And Skype properties also... I will be very happy if someone could suggest me and help me for both of the problems :)

P.S. And Also I forgot to mention that i cnanged alsa-base.conf file... Now it looks like that: 
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=3stack

---

### Post by cariboo on 2011-06-29
I hate to say it, but you are going at this the wrong way, you don't have to remove pulse in order to get Skype to work with most web cams and microphones. 

I would suggest reversing all the changes you made, and using alsamixer to set the volumes to where you need them.

You don't mention what type of system you are using, or if skype worked in Windows, so it's pretty hard to help without the proper information

---

### Post by jtarin on 2011-06-29
> My laptop is not recognising my headphones
Did they know each other in the past. Has your laptop had a head injury lately? Have you altered your headphones appearance radically from the norm? :p

---

### Post by neycheva87 on 2011-06-29
Yes, probably I am doing it the wrong way, but I needed a microphone and skype and I was too exausted ... So I tried this... I am a new one in using LINUX .... What do you mean by type of a system - the operating system is Ubuntu 10.10 (as said in my first sentence). Yes, my internal microphone worked without no problems on Vista - in all versions I have used - 3.8, and after that 5. So the only way to make a microphone work was to remove pulse - probably i should install it back? But how? I am not sure. My headphones are now working - I have chosen the wrong model of machine. 
Thank you in advance for everything!
> **cariboo907 said:**
> I hate to say it, but you are going at this the wrong way, you don't have to remove pulse in order to get Skype to work with most web cams and microphones. 

I would suggest reversing all the changes you made, and using alsamixer to set the volumes to where you need them.

You don't mention what type of system you are using, or if skype worked in Windows, so it's pretty hard to help without the proper information

---

### Post by neycheva87 on 2011-06-29
Yes, they were best friends... but now ... not that good friends. No, my laptop is in a good condition (it's not brand new so... ). What do you mean by "altering headphones appearance?? If it's what I think of - the answer is no ;) I am just new in Linux, not that new in computers ;) 
> **jtarin said:**
> Did they know each other in the past. Has your laptop had a head injury lately? Have you altered your headphones appearance radically from the norm? :p

---

### Post by smurphy_it on 2011-06-29
I think what ppl are asking of you is "what kind of computer you have".  We know the o/s, however no-one knows what kind of hardware they are dealing with here w/o some information.

So you could state what you have in your system, and then from a terminal run a "sudo lspci" and produce the output here.  That would be a good start.

---

### Post by neycheva87 on 2011-06-30
> **smurphy_it said:**
> I think what ppl are asking of you is "what kind of computer you have".  We know the o/s, however no-one knows what kind of hardware they are dealing with here w/o some information.

So you could state what you have in your system, and then from a terminal run a "sudo lspci" and produce the output here.  That would be a good start.
Haha, yes i think I missunderstood the question ;) Now it is more clear. I have a laptop - Acer TravelMate 5520G(Sorry that I have forgotten the technical details). 

Here is the output of the lspci-command: 
[I]
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)[/I]

---

### Post by jtarin on 2011-06-30
With your headphones plugged in open a terminal and issue the command  ```
alsamixer
``` adjust your headphones.

---

### Post by neycheva87 on 2011-06-30
> **jtarin said:**
> With your headphones plugged in open a terminal and issue the command  ```
alsamixer
``` adjust your headphones.
The problem for my headphones was when  I add a line in the alsa-base.confI have put a wrong model of the laptop. So my codec was ALC268, so I wrote model=3stack the first time. Now I changed it in model=acer-dmic and my headphones are working. The only thing that bothers me is that the quality of the microphone is very bad...

---

