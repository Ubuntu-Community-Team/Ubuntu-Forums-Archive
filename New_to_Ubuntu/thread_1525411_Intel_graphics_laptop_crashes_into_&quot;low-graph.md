---
title: "Intel graphics laptop crashes into &quot;low-graphics mode&quot; often"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by psadza on 2010-07-06
I am on Ubuntu 10.04 Lucid. I love the ease of Linux so far. My laptop worked from the get-go compared to issues with a WIN XP install. The laptop is a 2004 Toshiba Satellite M55-S135.

The issue is that at time my computer seems to go into terminal mode, and then I get a graphic option letting me run in low-graphics mode. I usually just restart, and all is fine. My graphics card is a:

systemicperformance@ubuntu:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)

However, Synaptic shows drivers installed for xserver-xorg-video-i740 and xserver-xorg-video-intel (for i800 and i900 chipsets), so I do not know if mine is i740 or i8/900.

Is there any advice on how to avoid this issue (lose some data at times, annoying)? I am very new to Linux, so I have a hard time following threads on terminal inputs of video graphics memory, etc... The above graphics output took me hours to find on the Ubuntu community, and I really don't know what the commands mean.

---

### Post by mikewhatever on 2010-07-07
You could try the workaround from the bug report below.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568127](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568127)
Open /etc/default/grub for editing:
```
gksudo gedit /etc/default/grub
```
add **i915.modeset=0** the 'GRUB_CMDLINE_LINUX_DEFAULT' line so that the final looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"
```
save and exit, then update grub with **sudo update-grub**
.

---

### Post by psadza on 2010-07-07
Thank you, I have made the change. I will see what happens. Interesting that the last part of the thread you mentioned seemed to show that the user removed this line, and that some other part of his fix seemed to work. However, I am too lost in all the text to figure out what beyond your recommendation was changed.

---

### Post by mikewhatever on 2010-07-07
Do you install software updates? Many of them are bug fixes, and who knows, one might provide a solution for you too.
PS: I forgot to mention it in the previous post, if you have desktops effects running, turn them off.

---

### Post by psadza on 2010-07-08
Yes, I install all updates. I will turn off effects.

I am having issues with the setting from above (grub edit). When I logged in today (perhaps the first reboot after the change) the external monitor resolution was low. When I increased it to 1900x1200, my mouse icon disappeared. I could also not get the monitor back to "same image on both monitors" as I could not get my laptop's wide screen monitor settings. The fix was to detach the external monitor cable. Once my laptop was the only monitor, then my mouse icon returned.

When I removed the "GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"and restarted, all is back to well.

I realise I did not share the external monitor set up in my original post. Does that have anything to do with the issue?

---

### Post by psadza on 2010-08-09
I have done a fresh install of Ubuntu 10.04. I still have this issue, where unexpectedly, my computer goes into a dialog about "low res" mode. I am too inexperienced to even be able to find the $xorg_backup_file it mentions making a log to. I have to reboot to fix things (ctrl + alt + del).

On my previous install, I seemed to be doing better, crashing only when powering off my external monitor. However, that dual-boot install crashed:
[http://ubuntuforums.org/showthread.php?t=1540149](http://ubuntuforums.org/showthread.php?t=1540149)

Is there a beginners' document for how to obtain all these log files everyone posts for additional information?

---

### Post by jtarin on 2010-08-09
Every once in awhile run the command ```
updatedb
``` it will take a minute oe so to finish, then you have access to ```
locate
``` which will help you find anything on your computer.

---

### Post by psadza on 2010-08-11
That command did not seem to work:
```
alamogroup@alamogroup-laptop:~$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'
alamogroup@alamogroup-laptop:~$ 
```

---

### Post by jtarin on 2010-08-11
> **psadza said:**
> That command did not seem to work:
```
alamogroup@alamogroup-laptop:~$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'
alamogroup@alamogroup-laptop:~$ 
```Preface the commands with "sudo" when you encounter language such as that from the terminal.

---

### Post by psadza on 2010-09-02
I continue to have intermittent graphics crashes. Sometimes after powering down / up external monitor manually, sometimes after external monitor wakes up from sleep, and sometimes with random application operations (latest was when I hit "send/receive" in Evolution email).

The attachments show the error messages. When I click okay on the first one (lately mouse click has not worked, so I have to us TAB and Enter keys), I get the options. However, all the troubleshooting, reconfig, etc, do not work. I just Restart X and reboot.


[IMG]file:///home/alamogroup/Desktop/IMG_0290.JPG[/IMG]

---

### Post by jtarin on 2010-09-02
Run ```
lsmod
``` in the terminal and post the output.

---

### Post by psadza on 2010-09-07
Here is the result...though I am currently traveling and NOT using my usual external monitor setup.

```

alamogroup@alamogroup-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 33024  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121792  0 
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
i915                  285586  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 ath5k
ath                     7611  1 ath5k
yenta_socket           20408  1 
drm_kms_helper         29297  1 i915
rsrc_nonstatic         10015  1 yenta_socket
cfg80211              126517  3 ath5k,mac80211,ath
drm                   162409  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24119  2 i915
psmouse                63245  0 
led_class               2864  1 ath5k
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
sky2                   40775  0 

```

---

