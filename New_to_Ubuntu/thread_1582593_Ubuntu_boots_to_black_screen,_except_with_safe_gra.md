---
title: "Ubuntu boots to black screen, except with safe graphics"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by flashinthedark on 2010-09-26
So I'm fairly new to Ubuntu and Linux in general. I managed to get Karmic installed and running fine on my desktop, but I remember having problems with my graphics card, an nVidia 9600GT. If I remember right, I had to change the display drivers that Ubuntu was using.
Anyway, a few months ago, I decided to upgrade to Lucid. I did and then everything broke. Now I cannot boot into Lucid from Grub at all. It looks like it is starting to boot (gives me some scrolling output), but then goes to a black screen and stays there. (Ctrl-Alt-F1 and Ctrl-Alt-F2 do nothing here). I've read about the trick where you add the nomodeset option to the boot options in place of quiet splash, but I can't seem to get that to work. 
Trying to boot from various ubuntu live CD's also fails with the same black screen. On those, I'm actually able to change the boot options correctly (as far as I know) and put nomodeset in place of quiet splash after hitting F6 to show the boot options. Changing those options does not help.
The only time I can get into Ubuntu at all is when I'm booting from a live CD and select the safe graphics option. This leads me to suspect that my video card is what's causing the issue here, but I really don't know what to do about it.
Any help would be utterly appreciated, as I have already spent many hours trying to find a solution. Thanks.

UPDATE 11/2/10----------

After much trial and error, I've now discovered that the video card was  indeed causing the problem, but I still don't know how. 

I found that unplugging the DVI cable leading to my second monitor from  the video card fixed the issue. That is, I can now boot into GParted  and, more importantly, Ubuntu without an issue. However, I know for a  fact that I've booted into Ubuntu in the past with both monitors plugged  in using a dual monitor setup. I want to figure out exactly what is  causing this problem so that I can go back to using both monitors in  Ubuntu.

Again, any help is much appreciated.

---

### Post by jtarin on 2010-09-26
Boot into Ubuntu and from the command line issue the command ```
lsmmod
``` and post the results. Let's see if it's loading the correct driver/module.

---

### Post by flashinthedark on 2010-09-26
Here's the results of that:

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
lp                      8964  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
mxl5005s               37116  1 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
s5h1409                 8864  1 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
tuner_simple           14832  1 
tuner_types            14396  1 tuner_simple
snd_seq_dummy           2656  0 
cs5345                  3568  1 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
tuner                  21540  1 
snd_rawmidi            22208  1 snd_seq_midi
dm_crypt               12928  0 
cx18                  108868  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
dvb_core               87364  1 cx18
i2c_algo_bit            5760  1 cx18
x_tables               16544  1 ip_tables
cx2341x                13440  1 cx18
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            17500  4 cs5345,tuner,cx18,cx2341x
videodev               36736  4 cs5345,tuner,cx18,v4l2_common
ppdev                   6688  0 
v4l1_compat            14496  1 videodev
tveeprom               11872  1 cx18
joydev                 10272  0 
rt2860sta             522456  1 
parport_pc             31940  1 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
parport                35340  3 lp,ppdev,parport_pc
psmouse                56180  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  1 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
floppy                 54916  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  0 
r8169                  32064  0 
mii                     5212  1 r8169
agpgart                34988  1 intel_agp

```

I forgot to mention this earlier, but I'm dual booting with Windows 7.

---

### Post by jtarin on 2010-09-26
Can you boot into Recovery Mode?
Here's some [documentation ]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")on 10.04 that could be realted to your problem.
Have you tried to install Ubuntu-restricted-drivers through Add/Remove Packages? It will detect your Graphics Card and install Nvidia driver.

---

### Post by flashinthedark on 2010-09-26
The Live CD that I have "doesn't have a dedicated Recovery mode" (according to the CD itself when I attempt to access recovery mode). 
The Live CD environment that I'm in now has offered to activate the nvidia proprietary drivers for me, but I've done that before and it doesn't seem to help, I'm guessing because it's not actually installing them to the HDD.

---

### Post by jtarin on 2010-09-26
> **flashinthedark said:**
> The Live CD that I have "doesn't have a dedicated Recovery mode" (according to the CD itself when I attempt to access recovery mode). 
The Live CD environment that I'm in now has offered to activate the nvidia proprietary drivers for me, but I've done that before and it doesn't seem to help, I'm guessing because it's not actually installing them to the HDD.
This is posibly because you need to get into the actual environment that your install is on and replicate this. Do you know how to "chroot" into your actual install?

---

### Post by flashinthedark on 2010-09-26
No, but it should be pretty simple, right?
Thanks for the help by the way.

---

### Post by jtarin on 2010-09-26
[Go here and scroll down to Method #3 CHROOT and use this]("https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling%20from%20LiveCD"). Skip steps 8,9 and 10. Do your work then finish with the remaining steps. You will need to get all your APT commands for installing the restricted drivers before you start as everything will be from the command line.You will be adding the repository for them then downloading and installing them.

---

### Post by flashinthedark on 2010-11-02
After much trial and error, I've now discovered that the video card was indeed causing the problem, but I still don't know how. 

I found that unplugging the DVI cable leading to my second monitor from the video card fixed the issue. That is, I can now boot into GParted and, more importantly, Ubuntu without an issue. However, I know for a fact that I've booted into Ubuntu in the past with both monitors plugged in using a dual monitor setup. I want to figure out exactly what is causing this problem so that I can go back to using both monitors in Ubuntu.

Again, any help is much appreciated.

---

### Post by flashinthedark on 2010-11-02
I found this link that might help me out. I'm going to try what it recommends:
[http://www.dwasifar.com/?p=862](http://www.dwasifar.com/?p=862)

---

