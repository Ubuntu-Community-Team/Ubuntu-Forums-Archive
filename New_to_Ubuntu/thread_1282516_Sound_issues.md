---
title: "Sound issues"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by takiama on 2009-10-04
I absolutely cannot get the sound on my Ubuntu installation working.  I have installed ALSA 1.0.21, and since I believe my audio device is the Intel High Definition Audio ICH9 Series, I tried to load the snd-hda-intel module, but I get an error.  I am completeley new to Ubuntu so I am not sure at all as to what I am doing.  I have posted previously reguarding this issue in the Hardware & Laptops section, but I figured I would post it here as well since I am an absolute beginner.  Can someone please help me determine which drivers/modules I need and how to install/load them?  I am also not 100% sure that my audio device is the Intel one, because on the Device Manager on my Windows Vista partition is has a VIA High Definition Audio(and something to do with SRS, but I believe that is software based).  However, I have recently been led to believe that it is the Intel one, but again, I am not sure.  So I need all the help I need in determining first of all what my issue is and then how to solve it. The original thread containing the error message and other information is here: [http://ubuntuforums.org/showthread.php?t=1282068](http://ubuntuforums.org/showthread.php?t=1282068)

Thanks in advance for any help.

---

### Post by LewRockwell on 2009-10-04
[http://linuxandfriends.com/2009/02/23/lshw-command-list-hardware-information-in-linux/](http://linuxandfriends.com/2009/02/23/lshw-command-list-hardware-information-in-linux/)

.

---

### Post by nhasian on 2009-10-04
to verify what sound chipset you have, use this terminal command:

```
lshw -C multimedia
```

can you download the Karmic Koala Beta ISO cd and use the LiveCD to boot to a desktop?  I'll bet your sound will work out of the box with the newer linux kernel.

---

### Post by takiama on 2009-10-04
Okay.  I will try to burn and boot a Live CD of the beta.  If that works I may just install that over my current partition.  In the meantime, here is the output from that command you posted:```
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 module=oss_hdaudio

```

I was correct about my audio device, now just to get it working...  I tried the oss_hdaudio it mentioned and it didn't work.

---

