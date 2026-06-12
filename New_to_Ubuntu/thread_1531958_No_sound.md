---
title: "No sound"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-15
I'm not getting any sound at all, from movies, music, nothing. I installed the driver for my radeon 5750hd and still nothing. Any suggestions. Someone suggest that i open alsamixer and move the sound bars up, i did that and nothing. And yes, i checked to see if it was on mute.

---

### Post by TimEnid on 2010-07-17
i followed the directions found [here]("https://help.ubuntu.com/community/SoundTroubleshooting"), and still nothing

---

### Post by sad_iq on 2010-07-17
Maybe it will be more usefull if you posted some info about your hardware...
can u post the result of ```
lspci
```,```
aplay -l
``` and ```
lsmod | grep snd
```
 Is your soundcard onboard? Are you trying to get audio from the hdmi output of your videocard?

---

### Post by gordon33 on 2010-07-17
TIm 

I have the same problem and followed the same trouble shoot sound directions.  I hope some one helps us.  here is what i get when i trouble shoot.

from "Are you in the sound group?"  (no sound from previous  mentioned checks.)

gordon@gordon-laptop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse
gordon@gordon-laptop:~$ ^C

Guide then said: "so I backed up then changed /etc/group:"    **What and Why?**


Skipping down to: "Is the system recognizing your sound card?"

gordon@gordon-laptop:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
gordon@gordon-laptop:~$ 

Then the guide said:

Your output should look something like this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


**Is my stuff okay?**

I will sto here until i get some feed back on what I have or don't have.

gordon33

---

### Post by rtlustyo on 2010-07-17
You could try installing the linux-backports-modules-alsa-generic meta-package.

---

### Post by TimEnid on 2010-07-17
> **sad_iq said:**
> Maybe it will be more usefull if you posted some info about your hardware...
can u post the result of ```
lspci
```,```
aplay -l
``` and ```
lsmod | grep snd
```
 Is your soundcard onboard? Are you trying to get audio from the hdmi output of your videocard?

lspci
> 00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: ATI Technologies Inc Device 68be
02:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:00.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
08:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
08:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
08:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
08:01.3 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)


aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lsmod | grep snd
> snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm

i have a radeon 5750hd card. my monitor and soundbar are plugged in via dvi cable. ibelieve i also have a soundcard onboard.

---

### Post by gordon33 on 2010-07-17
Hello rtlustyo

Why or how would that help?  My sound was working until late last night.

gordon33

---

### Post by TimEnid on 2010-07-17
> **rtlustyo said:**
> You could try installing the linux-backports-modules-alsa-generic meta-package.

how do i do that? thanks.

---

### Post by sad_iq on 2010-07-17
> **gordon33 said:**
> TIm 
gordon@gordon-laptop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse

This means you're not in the audio group...so you don't have access to any sound device. Your name should appear after **audio:x:29:pulse**
 In the terminal type: ```
fgrep -ie 'audio' /etc/group

``` just to recheck your name doesn't appear after pulse and ONLY if it DOESN'T type the following(don't change anything...just copy-paste):```
sudo cp /etc/group /etc/group_backup && sudo chmod a-wx /etc/group_backup && sudo adduser `whoami` audio
```
 Logout or reboot and see if it works...if not post the model of your laptop!

---

### Post by gordon33 on 2010-07-17
Hello

I have a HP G60t-200 lap top.

My name follows pulse now but still no sound.

gordon@gordon-laptop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,gordon
gordon@gordon-laptop:~$

---

### Post by sad_iq on 2010-07-17
> **TimEnid said:**
> how do i do that? thanks.

Open a terminal and type: ```
sudo apt-get install linux-backports-modules-alsa-`uname -r`
```
Logout or reboot...then go to System -> Preferences -> Sound and make sure the volume slider is not muted.

---

### Post by TimEnid on 2010-07-17
> **gordon33 said:**
> Hello

I have a HP G60t-200 lap top.

My name follows pulse now but still no sound.

gordon@gordon-laptop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,gordon
gordon@gordon-laptop:~$

same here

audio:x:29:pulse,tim

---

### Post by TimEnid on 2010-07-17
> **sad_iq said:**
> Open a terminal and type: ```
sudo apt-get install linux-backports-modules-alsa-`uname -r`
```
Logout or reboot...then go to System -> Preferences -> Sound and make sure the volume slider is not muted.

no go

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-alsa

---

### Post by gordon33 on 2010-07-17
Tim

Did the "sudo apt-get install linux-backports-modules-alsa-`uname -r`" 
help you.  Was your lap top's sound working before.

Gordon

---

### Post by gordon33 on 2010-07-17
Going out for dinner be back in about a hour and a half.

Gordon

---

### Post by TimEnid on 2010-07-17
> **gordon33 said:**
> Tim

Did the "sudo apt-get install linux-backports-modules-alsa-`uname -r`" 
help you.  Was your lap top's sound working before.

Gordon

it did not work. i am not on a laptop, its a pc i built. the motherboard is asus p6t. the sound works when i switch to windows 7 (which i dual boot with).

---

### Post by gordon33 on 2010-07-17
Tim


Thats interesting your sound works in windows.  My sound worked until i did an Update yesterday evening.

Gordon 

Will be back later

---

### Post by sad_iq on 2010-07-17
> **TimEnid said:**
> no go

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-alsa

Go to System -> Administration -> Software Sources in the **Ubuntu Software** tab make sure every box is checked (except the cd-rom related ones), the same should be in the **Other Software** and **Updates** tab, press **close**, a new window will appear...press **reload**. Then you should be able to upgrade your system and hopefully sound will be working after a reboot. Also... the package name is linux-backports-modules-alsa-lucid-generic sry for the mistake :( You can install it from synaptic after you upgrade and reboot your system.

---

### Post by TimEnid on 2010-07-17
> **sad_iq said:**
> Go to System -> Administration -> Software Sources in the **Ubuntu Software** tab make sure every box is checked (except the cd-rom related ones), the same should be in the **Other Software** and **Updates** tab, press **close**, a new window will appear...press **reload**. Then you should be able to upgrade your system and hopefully sound will be working after a reboot. Also... the package name is linux-backports-modules-alsa-lucid-generic sry for the mistake :( You can install it from synaptic after you upgrade and reboot your system.

that didnt work either. there were no boxes unchecked under Ubuntu Software (just "source code, which has a "-" next to it.). Under other software there were 3 boxes unchecked. i checked them all, Updates had everything checked. I typed that command into terminal and got 
"linux-backports-modules-alsa-lucid-generic: command not found

i just did an update and i am restarting again.

---

### Post by TimEnid on 2010-07-17
still nothing.

---

### Post by sad_iq on 2010-07-17
> **TimEnid said:**
>  I typed that command into terminal and got 
"linux-backports-modules-alsa-lucid-generic: command not found

i just did an update and i am restarting again.

The command is ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic 
```
Reboot after that...if it still doesn't work...I'm clueless for now...it's 01:07 here...waaaay past my bedtime :(
 There is a post about updating alsa... [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) maybe that can help?

---

### Post by TheStroj on 2010-07-17
I never tried lubuntu and I'm not sure how things go around there, but do you have codecs installed? because they don't come by default in Ubuntu.

This could help:
[http://lubuntu.net/blog/lubuntu-screencasts-codecs](http://lubuntu.net/blog/lubuntu-screencasts-codecs)

A common problem by me and my friends was a permission problem - yes, you can set that you don't have permission to use audio devices (or something like that). 

To fix that, go to System -> Administration -> Users & groups -> Advanced Settings -> 'type password' -> go to tab 'User Permissions' and on the bottom is that option.

Btw, I'm using slovenian language pack so I maybe didn't translate good, but you will find it, I think I didn't translate that bad :P.

Also, it might not be exactly the same in Lubuntu, but things are kinda similiar, just search around a bit :)

Hope any of these help!

---

### Post by TimEnid on 2010-07-17
> **sad_iq said:**
> The command is ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic 
```
Reboot after that...if it still doesn't work...I'm clueless for now...it's 01:07 here...waaaay past my bedtime :(
 There is a post about updating alsa... [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) maybe that can help?
still nothing. thanks for the help though. i will check out that thread.

> **TheStroj said:**
> I never tried lubuntu and I'm not sure how things go around there, but do you have codecs installed? because they don't come by default in Ubuntu.


yes, i have the codecs installed.

---

### Post by TimEnid on 2010-07-17
wooo hooo, i got it to work. i went into the mixer, and then Output, instead of selecting my hdmi audio, i selected Internal Audio Analog, and the sound started to come out. thanks for everyones help

---

### Post by gordon33 on 2010-07-17
Hello Tim

How did you get to the mixer, and then Output, instead of selecting my hdmi audio, i selected Internal Audio Analog?

Gordon

---

### Post by TimEnid on 2010-07-17
> **gordon33 said:**
> Hello Tim

How did you get to the mixer, and then Output, instead of selecting my hdmi audio, i selected Internal Audio Analog?

Gordon

prefernces>sound>hardware. theres two options there. on for internal audion, and another that says juniper hdmi audio.

---

### Post by gordon33 on 2010-07-17
Tim

Thank You, Thank you!

I had to chose "Analog Stereo Output.  I have sound now.

Thank you all.

---

### Post by TimEnid on 2010-07-17
> **gordon33 said:**
> Tim

Thank You, Thank you!

I had to chose "Analog Stereo Output.  I have sound now.

Thank you all.

great. it probably was one of the suggestions that were provided that helped us. We just had to make this change.

---

