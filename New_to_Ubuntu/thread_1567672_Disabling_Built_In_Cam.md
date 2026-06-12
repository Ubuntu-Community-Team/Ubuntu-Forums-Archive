---
title: "Disabling Built In Cam"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by vimorest on 2010-09-04
Am I the only worried parent about gmail, pidgin, empathy, skype, etc showing to everybody what sound / cam capacity my computer has? As a parent of two teenagers, this really worries me. 

The problem is that I am new to Ubuntu and have no idea how to disable it.  I want this cam to be permanently disabled (as in it is not there at all), and I don't even care if it breaks the damn webcam. I don't want any messenger showing that my daughters have webcam available. How can I turn this off forever? 

Thank you.

Oh... lsusb gives me:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


And lsmod gives me: 


Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_idt      61450  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_hda_intel          25677  2 
softcursor              1565  1 bitblit
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
vga16fb                12757  0 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
vgastate                9857  1 vga16fb
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
arc4                    1473  2 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
joydev                 11072  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                121641  0 
snd_timer              23649  2 snd_pcm,snd_seq
iwlcore               124955  1 iwlagn
i915                  321686  2 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62467  0 
drm_kms_helper         30742  1 i915
hp_accel               12168  0 
videodev               40518  1 uvcvideo
lis3lv02d               7648  1 hp_accel
snd                    71106  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   199268  3 i915,drm_kms_helper
psmouse                64576  0 
lirc_ene0100            7532  0 
input_polldev           3106  1 lis3lv02d
v4l1_compat            15495  2 uvcvideo,videodev
mac80211              238448  2 iwlagn,iwlcore
soundcore               8052  1 snd
cfg80211              148546  3 iwlagn,iwlcore,mac80211
i2c_algo_bit            6024  1 i915
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  1 i915
serio_raw               4918  0 
lirc_dev               11302  1 lirc_ene0100
output                  2503  1 video
led_class               3764  2 iwlcore,hp_accel
intel_agp              29095  2 i915
v4l2_compat_ioctl32    12020  1 videodev
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  0 
r8169                  39650  0 
mii                     5237  1 r8169
ahci                   37870  3

---

### Post by redbook4574 on 2010-09-04
I would think your only option would be in bios.

---

### Post by vimorest on 2010-09-04
Thank you for your reply. I was afraid of that.

Unfortunately, I have no idea how to do that and I have even tried to find the cam in BIOS to no avail. And since I'm not really sure of what I'm doing there, I'm afraid to do something wrong and create a bigger problem by breaking something I need. 

I was trying to avoid reinstalling windows just because of that, but before, I could just disable the cam and there was no issue. Now with Ubuntu, my daughters (9 and 12) are being constantly pressured by peers and even strangers for cam sessions. The easy way out of it ("my cam doesn't work") is no longer effective, since everybody can see that a camera is available, and the conversations always go back to "but I see that you have cam, just turn it on". I feel this is terribly unfortunate and a huge privacy issue. It has become an issue in our home. Now I'm in a difficult position because as much as I love Ubuntu, I can't allow this, and I can't supervise them 24/7. I feel they are much too young to face this type of pressure, so if somebody can help it would be much appreciated.

---

### Post by _Fordy on 2010-09-04
The only way to "absolutely disable it forever", in any OS, is to - as you say you are happy with - physically break it.

I presume it's a laptop/netbook in question as if it's a desktop just unplug it!!

If it's built into the screen surround on a laptop however, and you really are worried and don't mind breaking it, stick a pin in. If necessary, lay the laptop down on the screen half, screen side up and gently hammer the pin in.

If however, you would like to preserve the webcam for resell value or whatever, **simply take a permanent marker and put a dot right over it.**

---

### Post by no2498 on 2010-09-05
i do not know if skype or the others use adobe flash
but if they do you can block all websites 
go to adobe and find the settings manager


hope this helps

---

### Post by Christian Knudsen on 2010-09-05
I found this:

[http://www.zzillezz.net/2008/09/24/disable-webcam-in-ubuntu/](http://www.zzillezz.net/2008/09/24/disable-webcam-in-ubuntu/)

But I'm not sure if that only applies to Acer laptops...

---

### Post by no2498 on 2010-09-05
type in webcam in a terminal see if you use gspca

---

### Post by S.R on 2010-09-05
This one is easy breezy. Find the manual or there is never a shortage of how to videos on youtube. Disassemble the screen bezel (guitar pick works well) taking care not to mess up up Wi-Fi wires and physically remove or just snip the wires to the cam.

If you are uncomfortable doing that then take it to a local computer shop where they can do it for you.

For the love of god though don't go hammering anywhere near your screen.

---

### Post by sandyd on 2010-09-05
usually, the webcam appears as /dev/video0 (check before doing what I suggest!!!!)
If it does,
just do
```

rm /dev/video0
```each time the computer starts up.

you can add it to the rc.local file (I think its called rc.local, im not sure since I don't have one)

```

sudo nano /etc/rc.local
```add the following line

```

/bin/bash -c /bin/rm /dev/video0
```you could also do this using udev rules (they control the detevtion, and adding of hardware into the /dev directory), but thats more difficult, and you have no idea how many things can go on when you mess with the rules....

you could also remove the entire driver from the kernel, but still, its much ado about a small issue.....

---

### Post by Paqman on 2010-09-05
> **_Fordy said:**
> 
If however, you would like to preserve the webcam for resell value or whatever, **simply take a permanent marker and put a dot right over it.**

A sticky dot would work just as well, and be easier to remove if you wanted.

---

### Post by sandyd on 2010-09-05
> **Paqman said:**
> A sticky dot would work just as well, and be easier to remove if you wanted.
postitnote :D

---

### Post by dacman48 on 2010-09-05
open u the comp and rip the camera offf the mobo :)

---

### Post by linux18 on 2010-09-05
duct tape

---

### Post by Thryn on 2010-09-05
In Skype at least, you can make it not show that you have a camera.

Options > Video and then either uncheck the enable video with Skype box (or whatever it's called) or check the one to show no one that you have a camera. I don't see an option to do that with sound.

And I sympathise... Skype is creepazoid land. I recommend making sure they haven't checked 'female' in their profiles because it seems to increase the unwanted attention.

---

### Post by DukeOfMixture on 2012-12-06
Silly putty

---

### Post by abandoned45623409 on 2013-02-08
[COLOR=#333333]I once had to disable temporarily the built-in webcam in my laptop. He is what I did:[/COLOR]
 
[COLOR=#333333]First, I used following command to list the devices (my built-in webcam happens to be connected via internal USB):[/COLOR]
```
find /sys/ -path "*usb*product*" -exec ls {} \; -exec cat {} \; 2> /dev/null
```[COLOR=#333333]It prints a series of paths and devices associated with the paths - in my case:[/COLOR]```
/sys/devices/pci0000:00/0000:00:1a.0/usb1/product
EHCI Host Controller
/sys/devices/pci0000:00/0000:00:1d.0/usb2/product
EHCI Host Controller
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/product
HP HD Webcam [Fixed]
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input5/id/productb230/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/product
HP Integrated Module
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/produc
tEMV Smartcard Reader
```[COLOR=#333333]The path I'm looking for is [/COLOR]*/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/product*[COLOR=#333333] - when I run following command as root, the webcam will be disabled (until the next restart):[/COLOR]
```
echo 1 > /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/remove
```

---

### Post by wildmanne39 on 2013-02-08
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

