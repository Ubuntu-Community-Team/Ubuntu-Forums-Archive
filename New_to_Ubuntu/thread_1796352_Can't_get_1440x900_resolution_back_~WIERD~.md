---
title: "Can't get 1440x900 resolution back ~WIERD~"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Glupoi652 on 2011-07-03
I start my computer up one day to find that my resolution is back at 1024x768.  I try for several days to get it back, reinstalling ubuntu, etc.  I found that the proprietary driver that I use "is not currently in use", and I can't get it to use that proprietary driver.  Instead, it is using some other driver (not nouveau or whatever it is, I checked).  

Details:  
Card:  GTS 450
Installed packages:  
nvidia-current
nvidia-settings
nvidia-common
OS:  Ubuntu 11.04

I have tried dpkg-reconfigure -phigh xserver-xorg (or something of that sort), sudo nvidia-xconfig (which sometimes either sets me to 600x480 res or back to 1024x768 res), fiddling with the xorg.conf settings all helped me either minimally or not at all, or just plain destroyed my install.  Please help, I want my drivers to be back in order, and I want to be able to select 1440x900 res from the resolution list.  

and btw, what I did in the xorg.conf file was make backups, add Modes "1440x900" under section Screen subsection Display.  

Please help me in this strange time of need!

---

### Post by Psyco430404 on 2011-07-03
launch the driver utility and install the recommended driver, from their reboot, and once it starts again, go to system>admin>nvidia xorg settings manager. (or something like that) From their you can set your resolution and save it to your xorg config file.

---

### Post by Glupoi652 on 2011-07-03
Tried that hundreds of times, but no cigar so to speak.

---

### Post by jtarin on 2011-07-03
Try using [xrandr.]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

---

### Post by nerdy_kid on 2011-07-03
please zip all files in /etc/modprobe.d/ and post them here.  Also, please run lsmod and post the output here.

---

### Post by Glupoi652 on 2011-07-03
Here is my lsmod output

```

Module                  Size  Used by
nls_utf8               12493  1 
udf                    83795  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  4 
nvidia               9766978  38 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio          91410  1 
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13274  2 snd_hda_codec,snd_usb_audio
arc4                   12473  2 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt61pci                27265  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
crc_itu_t              12627  2 udf,rt61pci
rt2x00pci              13986  1 rt61pci
joydev                 17322  0 
uvcvideo               66851  0 
rt2x00lib              39075  2 rt61pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
videodev               75143  1 uvcvideo
asus_atk0110           17664  0 
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi
cfg80211              156212  2 rt2x00lib,mac80211
snd                    55295  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
psmouse                59039  0 
eeprom_93cx6           12653  1 rt61pci
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
hid_logitech           17421  0 
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
hid                    77084  2 hid_logitech,usbhid
floppy                 60032  0 
atl1e                  32576  0 
pata_marvell           12756  0

```I have attached modprobe.d file.

---

### Post by jtarin on 2011-07-03
And how is "xrandr" working out for you?:p

---

### Post by Glupoi652 on 2011-07-03
xrandr:  Failed to get size of gamma for output default.  Don't you just love errors! lol

---

### Post by jtarin on 2011-07-03
Have you tried with the driver downloaded from nvidia.com?
What version of Ubuntu? 32 or 64 bit?

---

### Post by Glupoi652 on 2011-07-03
32 bit, and last time I downloaded something from nvidia, I had to reinstall ubuntu.

---

### Post by wildmanne39 on 2011-07-04
> **Glupoi652 said:**
> 32 bit, and last time I downloaded something from nvidia, I had to reinstall ubuntu.Hi, I would manually set resolution with xorg, that is what I had to do, it has been a while though, here is a guide to help.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)
this is the method used when xrandr fails.

---

### Post by jtarin on 2011-07-04
Configuring your xorg file by hand used to be standard setup in Linux....we've lost the skill.

---

### Post by wildmanne39 on 2011-07-04
> **jtarin said:**
> Configuring your xorg file by hand used to be standard setup in Linux....we've lost the skill.I heard that, it is not as common, but it has been needed more with natty.

---

### Post by nerdy_kid on 2011-07-04
do:

```

sudo apt-get --purge remove nvidia*

echo "blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nv
" | sudo tee /etc/modprobe.d/nvidia-graphics-drivers.conf

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.trash

sudo apt-get install nvidia-current

sudo nvidia-xconfig

sudo update-initramfs -u

sudo reboot

```

That purges your nvidia drivers, blacklists nouveau and other drivers you dont want messing with your Xorg, backs up and resets your xorg.conf file, installs the correct nvidia drivers, updates the initial ram file system, and reboots the system.  Please do all of the commands, even if you have tried them before.  After the system has rebooted, open a terminal and run nvidia-settings -- the nvidia control panel should open, click "X server display configuration" and select your desired resolution from the resolution from the drop down.

---

### Post by Glupoi652 on 2011-07-04
OK, After following some steps, I have millions of backups of xorg.conf, I have nvidia-current "activated" but not currently in use.  when I installed it, I tracked down the readme, and I did find my GPU as supported, now I think the problem is that the driver is not activated, I just need to know how to fix that jockey bug so I can activate that bloody driver.  

Right now, I have nvidia-current activated but not implemented (need to know how to fix this)

My plan will be this checklist:  

If I get enough 3D acceleration to run minecraft respectively well, but do not get 1440x900 res, I will retry with the editing of xorg.conf (and hopefully not break the install)

If I get 1440x900 res but don't get a driver that can be implemented, I will continue my search for a driver... and if I get desperate enough, I will retry noveau even though that broke my install last time.  

If I get 1440x900 and can play minecraft respectively well, I will change the status of this post to [Solved]

and btw, BUMP

---

### Post by nerdy_kid on 2011-07-04
did you do what I said in my last post?

What happens when you start nvidia-settings?

---

### Post by Glupoi652 on 2011-07-04
Good news, minecraft works fine... now to force the resolution

and yes I did what you suggested, but at least it had some success, the code that you gave me made the computer activate the correct driver, but it is not implemented (again, I looked up why, and it is a bug in jockey).  Now, I will look up how to force the resolution with some of the earlier posts.  

When I open up the nvidia-settings, the highest resolution that it will allow me is 1360x768, which makes my screen look weird, so I don't implement that.

---

### Post by wildmanne39 on 2011-07-04
> **Glupoi652 said:**
> Good news, minecraft works fine... now to force the resolution

and yes I did what you suggested, but at least it had some success, the code that you gave me made the computer activate the correct driver, but it is not implemented (again, I looked up why, and it is a bug in jockey).  Now, I will look up how to force the resolution with some of the earlier posts.  

When I open up the nvidia-settings, the highest resolution that it will allow me is 1360x768, which makes my screen look weird, so I don't implement that.
Hi, if you activated the driver and you can see the unity deaktop then your driver is activated, the bug is that is shows not being used when it really is. Also I have to use the old driver for my card the 173, the new one caused all kinds of problems. also if you still have lag go to this link and it usually fixes the problem.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by nerdy_kid on 2011-07-04
> **Glupoi652 said:**
> Good news, minecraft works fine... now to force the resolution

and yes I did what you suggested, but at least it had some success, the code that you gave me made the computer activate the correct driver, but it is not implemented (again, I looked up why, and it is a bug in jockey).  Now, I will look up how to force the resolution with some of the earlier posts.  

When I open up the nvidia-settings, the highest resolution that it will allow me is 1360x768, which makes my screen look weird, so I don't implement that.

ok, so the nvidia driver is active.  Now just add the resolution line that you added to /etc/X11/xorg.conf.trash back into /etc/X11/xorg.conf and logout and back in and you should be good.

---

### Post by Glupoi652 on 2011-07-04
I have tried code:  

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes     "1440x900" "1360x768" "1152x864" "1024x768" "800x600" "680x384" "640x480" "512x384" "400x300" "320x240"
    EndSubSection
EndSection

I tried that code and that nearly destroyed my installed.  

Pretty much, it was 1440x900 + every other mode that was available.  I also did 

Modes     "1440x900"...
that also nearly killed my install too.  WHAT DO I DO??????

Bump

---

### Post by jtarin on 2011-07-04
Run this command and post the output```
sudo get-edid | parse-edid
```

---

### Post by Glupoi652 on 2011-07-05
Since the 1440x900 resolution doesn't even exist on my windows xp partition, I am assuming its a hardware issue... I'll contact PNY later today to see if I can RMA it.

---

