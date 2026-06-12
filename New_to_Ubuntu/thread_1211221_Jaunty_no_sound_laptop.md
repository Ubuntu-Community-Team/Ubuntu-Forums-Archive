---
title: "Jaunty no sound laptop"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-07-12
I have just installed Jaunty (dual boot) on my intel based laptop but no sound. Have tried all previous suggestions but no luck . Sound o.k. in windows . Could use Jaunty without sound but would like to get it working .

---

### Post by halitech on 2009-07-12
what kind of laptop?

can you post the results of```
lshw -C sound
``````
lspci
``````
aplay -l
```

---

### Post by ex-wirecutter on 2009-07-12
Compaq Presario 2700

---

### Post by ex-wirecutter on 2009-07-12
multimedia            
       description: Multimedia audio controller
       product: 82801CA/CAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
len@len-laptop:~$

---

### Post by northern lights on 2009-07-12
> **halitech said:**
> ```
lshw -C sound
```
Must have gotten mixed up here. '*sound*' is not a valid class - you're looking for '*multimedia*'.

Please post the output of```
sudo lshw -C multimedia
```plus *aplay -l* as requested by halitech.

---

### Post by ex-wirecutter on 2009-07-12
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
len@len-laptop:~$

---

### Post by ex-wirecutter on 2009-07-12
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
len@len-laptop:~$ sudo lshw -c multimedia
[sudo] password for len: 
  *-multimedia            
       description: Multimedia audio controller
       product: 82801CA/CAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master

---

### Post by halitech on 2009-07-12
> **northern lights said:**
> Must have gotten mixed up here. '*sound*' is not a valid class - you're looking for '*multimedia*'.

Please post the output of```
sudo lshw -C multimedia
```plus *aplay -l* as requested by halitech.

not confused unless ubuntu took it out cause here's mine on Debian

```
daryl@debian:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
daryl@debian:~$
```

---

### Post by halitech on 2009-07-12
none the less, hardware looks like it is being seen fine. Have you checked alsamixer to make sure nothing is muted?

---

### Post by ex-wirecutter on 2009-07-12
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ex-wirecutter on 2009-07-12
Have checked alsa mixer . nothing muted , all controls turned up full

---

### Post by gamerchick02 on 2009-07-12
Hey there.

I know this is a very simple check, but have you made sure you don't have the "external amplifier" checked?

On my Gateway, I noticed that was the biggest issue.

Good luck!

Amy

---

### Post by ex-wirecutter on 2009-07-12
Thanks for your suggestion , where do I find that option ?

---

### Post by ex-wirecutter on 2009-07-12
Thanks everyone , I will just have to keep trying or use it without sound .

---

### Post by halitech on 2009-07-12
did you run alsamixer from the terminal? it should be listed there if it has it. you might also need to mute the headphones to get sound out of the onboard speakers.

---

### Post by ex-wirecutter on 2009-07-12
Everything seems to check out o.k. but no sound . Never mind I can always use windows for sound , or , perhaps try Hardy , never had any trouble with that .

---

### Post by gamerchick02 on 2009-07-12
> **ex-wirecutter said:**
> Thanks for your suggestion , where do I find that option ?


Right click on the volume icon on your panel, and click on "volume control".  Click on the "switches" tab, and there should be a switch for "external amplifier".

If there is no "switches" tab, enable it by hitting the "preferences" button and check the "external amplifier" button.  Then you should be able to go to the "switches" tab.

Make sure the checkbox by external amplifier isn't checked.  Hit close, and you should be set.

Amy

---

### Post by aysiu on 2009-07-12
I had this problem, and this was the fix:
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44)

---

### Post by ex-wirecutter on 2009-07-14
Thanks for the suggestion but external amplifier is not checked .
I think the problem may be with alsa mixer attenuating the sound , I had this on my desktop pc and had to use an amplifier . Is there any alternative to alsa mixer ?

---

