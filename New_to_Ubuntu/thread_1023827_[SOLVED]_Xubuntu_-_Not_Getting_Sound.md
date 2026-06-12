---
title: "[SOLVED] Xubuntu - Not Getting Sound"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by LNB on 2008-12-28
Hello everyone.  I've been looking through the sound issues posts on this forum but would like to ask for additional assistance to get sound to come through on my system.  Very new to Linux, so would be greateful for your help.  Thank you.

I've looked through this thread, but have not been successful:

[_http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")_

I've tried variations of the alsa-basis edit using "options snd-hda-intel model=XXX" by varying XXX to different configurations, rebooting, and then playing a sound with no luck.  Have tried ref, dell, and the ones suggested in the Alsa-Configuration.txt under the STAC9220/9221 in the snd-hda-intel module.

Some system outputs:

System: Dell Dimension 5100, 2.5GB RAM, Intel Pentium 4 2.8 Ghz x2
OS: Xubuntu 8.10 Intrepid

[INDENT]LNB@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

LNB@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/INDENT]

**Codec:**

```
LNB@ubuntu:~$ cat /proc/asound/card0/codec#*
Codec: SigmaTel STAC9221 A1
Address: 0
Vendor Id: 0x83847680
Subsystem Id: 0x102801ab
Revision Id: 0x103201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x47 0x47]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x0e 0x0e]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x1f 0x1f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x1d 0x1a]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x17
  Processing caps: benign=0, ncoeff=0
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x18
  Processing caps: benign=0, ncoeff=0
Node 0x08 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=5, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x09 [Audio Input] wcaps 0x140311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x11
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=30, enabled=1
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01813024: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0x4
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN Detect
  Pin Default 0x01a19021: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect Trigger ImpSense
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x01452130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Grey
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 3
     0x08* 0x17 0x19
Node 0x11 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  EAPD 0x0:
  Pin Default 0x40000100: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 3 samples
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15* 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x0e 0x15* 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x02a19320: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x16 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 4
     0x02* 0x03 0x04 0x05
Node 0x17 [Audio Selector] wcaps 0x300903: Stereo Amp-In R/L
  Amp-In caps: N/A
  Amp-In vals:  [0x86 0x86]
  Connection: 1
     0x12
Node 0x18 [Audio Selector] wcaps 0x300903: Stereo Amp-In R/L
  Amp-In caps: N/A
  Amp-In vals:  [0x87 0x87]
  Connection: 1
     0x13
Node 0x19 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
  Delay: 3 samples
Node 0x1a [Audio Output] wcaps 0x30201: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  Delay: 3 samples
Node 0x1b [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x40000100: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x1a

```
**Current Alsa-Basis File:**
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

options snd-hda-intel model=ref
```

---

### Post by linux_tech on 2008-12-28
Did you try -
options snd-hda- intel model=dell-3stack

---

### Post by linux_tech on 2008-12-28
Try stopping and restarting alsa

```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```
Gnome-alsamixer can be a bit easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type
```
gnome-alsamixer

```
check all settings, make sure nothing is muted and volume is up

---

### Post by LNB on 2008-12-28
Thank you for your response.   Tried both of your suggestions, but no sound still.  

With respect to restarting ALSA: the only thing that changed seems to be the appearance of the desktop.  The GNOME ALSA Mixer does seem more user friendly and I made sure that none of the "mute" options were clicked.

---

### Post by eagle416 on 2008-12-28
I ran xubuntu and had a problem too.

Check here.
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by linux_tech on 2008-12-28
Try restarting pulseaudio:

In a terminal:
```
sudo killall pulseaudio
```

then hit Alt+F2, and type:
```
pulseaudio
```

---

### Post by altonbr on 2008-12-28
> **linux_tech said:**
> Try restarting pulseaudio:

In a terminal:
```
sudo killall pulseaudio
```

then hit Alt+F2, and type:
```
pulseaudio
```

I have no audio and I receive this error when I run that command:
> **The command "pulseaudio" failed to run:**

Failed to execute child process "pulseaudio" (No such file or directory)

---

### Post by linux_tech on 2008-12-28
> **altonbr said:**
> I have no audio and I receive this error when I run that command:
see Pulseaudio how to here-
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by altonbr on 2008-12-28
> **linux_tech said:**
> see Pulseaudio how to here-
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I appreciate that, but every tutorial I've ran doesn't work.

Ubuntu can play my audio just fine, but something is simply missing in Xubuntu.

---

### Post by LNB on 2008-12-28
Thanks for the suggestion Linux_Tech.  I tried your latest suggestion, but it appears that I do not have pulseaudio.  Is that something I need to install?

```
lnb@ubuntu:~$ sudo killall pulseaudio
[sudo] password for lnb: 
pulseaudio: no process killed

lnb@ubuntu:~$ pulseaudio
The program 'pulseaudio' is currently not installed.  You can install it by typing:
sudo apt-get install pulseaudio
bash: pulseaudio: command not found
lnb@ubuntu:~$ 

```

Eagle416, thank you also.  I'll start going through your sound guide.  Much appreciate it.

---

### Post by LNB on 2008-12-28
Ok, I'm retracing my steps up to this point to see if I missed something more basic.  I ran "lspci -v" and got several results, including the audio info below:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01ab
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
I see that my _chipset_ is part of the ICH7 family, which is listed as compatible in the ALSA SoundCard Matrix here:

[_http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel_]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

BUT, I don't see the exact _product_ listed.  Does this simply mean that my onboard soundcard is not supported?  Thanks.

---

### Post by LNB on 2008-12-28
Guys, thanks very much for your help.  I kept working on the problem using the guide from earlier, referenced here again, and was able to successfully get sound to come out of my speakers...

The guide again:

[_http://ubuntuforums.org/showthread.php?t=205449_]("http://ubuntuforums.org/showthread.php?t=205449")

Here is what did it for me:

1) Changed the alsa-base options back to "options snd-hda-intel model=ref"

2) _Loaded_ the sound driver/module:
```

sudo modprobe snd-hda-intel
```

3) Added the module to the end of the following:
```

 sudo nano /etc/modules
```

4) After I did this, I reran the GNOME-ALSA Mixer and saw that a new "Side" speaker option had appeared along with a ICE958 toggle.  I _unmuted_ the "Side" speaker option, and clicked on the ICE985 toggle.

5) Rebooted and played a sound!

Btw, I find it pretty cool that you are able to turn on/off the side speakers and the front headset sounds independently.  Not that I would ever need that level of customization, but didn't even think that this was possible in Windows.   Thanks again guys, learned a lot about LINUX this afternoon...

---

