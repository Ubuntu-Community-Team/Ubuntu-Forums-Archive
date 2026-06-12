---
title: "Sound works, except ..."
date: 2010-04-17
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-04-17
Recently installed 9.10.  Testing shows that video files yield sound from my speakers when played by various players, CDs play sound with Rhythmbox, web sites play sound with (presumably) Flash Player.  Line In does not yield sound.

On this computer (DFI Lanparty NF4 SLI) with Realtek Karajan sound module running under Win2k, a signal on Line In always yields sound output unless deliberately blocked with the mixer, independent of whatever else is running or playing.  As I can "easily" swap drives to change between OS, I can confirm that the Line-In signal source is present.

System/Preferences/Sound GUI has nothing muted and all levels are high enough to provide output if there will be any.

I have gone into alsamixer playback GUI, found the Line In set to zero level and boosted it up without effect on speaker output.  I have turned up the master gain without effect.  I have gone into the capture GUI (via F4) and meddled there without effect.  (The Line-In was set to capture.)

Alsamixer reports on the playback screen
   Card: NVidia CK804                                                           &#9474;                                  Chip: Realtek ALC850 rev 0                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-6.00, -6.00]

uname -a reports:[INDENT]Linux kirby-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
[/INDENT]aplay -l reports:[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]alsactl -v reports:[INDENT]alsactl version 1.0.20
[/INDENT]lspci reports:

```
 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
 
```The only other anomaly that I've learned enough from this forum to find is in the file asound.state from which a snippet follows:

```

     control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value false
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 22
        value.1 22 

```The volume seems consistent with the view presented by the Line In element of the alsamixer GUI, but the "Line Playback Switch" seems to be off.  I don't see any way in alsamixer to turn it on, nor do I know that is the problem, other than the working sound sources have their switches in TRUE state. 

Help is appreciated.

Thanks

kirby

---

### Post by KirbySmith on 2010-04-19
bump

---

### Post by lidex on 2010-04-19
Here is a screen of my alsamixer displaying capture devices. If I scroll to the right with the arrow keys to the "Input Source" options, I can use the up/dn arrows to toggle between mic/front mic/line. Use the tab key to select the view - or also F4 in my case.

---

### Post by KirbySmith on 2010-04-20
Lidex, thanks for the response.  I seem to have a somewhat different schema under alsamixer capture (F4).  Most importantly, perhaps, I don't have the "Input Source" control that you show allowing switching between inputs within the same control.  Instead, I have several different controls (without gain) that can be individually turned on or off.

Since I haven't figured out with ubuntu how to do window image captures yet (haven't investigated Snagit-like software), I'll have to try with words.

My Capture GUI seems a bit odd, relative to the Playback GUI.  The left most control is "Line" and shows "CAPTUR" above it in red, along with L and R.  However, there is no volume control "thermometer" as there is on some other controls, and I haven't found any way to force one.

Eight shifts farther to the right is a control called "Capture" that does have a volume control that is up.  However, unlike your example, it doesn't say CAPTUR under it.  Using the space bar per 'man alsamixer', I turned capture on for the Capture control.  It remained on for the Line control at the far left.  However, this action has not produced any sound.

Using the space bar to move capture from line to CD or whatever has no effect on passing sound from Line-In.

I have considered changing the value of the asound control.18 to true as an experiment, but the experiment won't be useful if some command is needed to make asound.state update some other file.

kirby

---

### Post by lidex on 2010-04-20
I would try updating alsa. You can find the link for the upgrade script in my sig.

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
Check that it's not muted in Pulse as well. Applications>Sound and Video>PulseAudio Volume Control

---

### Post by lidex on 2010-04-21
KS, BTW, try installing Shutter for screen capture. Should be in the repos.
```
sudo apt-get install shutter
```
Defaults are 
```
PrtScr = Fullscreen Cap
Alt+PrtScr = Selection
Selection options = Selection/Window/Section
```

---

### Post by KirbySmith on 2010-04-21
Thanks for the help so far. I'll get back with results as soon as work allows.
 
kirby

---

### Post by KirbySmith on 2010-04-21
I'll have to attack these suggestions piece-wise.

Starting with the easiest, Applications / Sound & Video / Pulse Audio Volume Control *does not exist* on my menu.  Under System/Preferences/Sound there are several audio controls, but they are all turned up to the 100% mark.  These are the same controls that are reached via the speaker icon on the top bar to the right.

There is Applications/Sound&Video/AlsaMixerGUI (I may have installed that at some time, don't recall) that generates a window called ALSA Mixer on which is the label Card Pulse Audio.  (Not that I actually have that card.)  

There are two sets of two controls in this window, unlike the multiplicity of controls in the terminal form of alsamixer.  On pair is called Master and the other Capture.  All four are at around 70%.  I recall them being different a week or so ago, so messing with the terminal form of alsamixer probably changed them.

Interestingly, right clicking on the ALSA logo in this window yields a screen labeled /proc/asound.  This screen doesn't admit to copying directly as text.  I'll have to get shutter to grab it.  Proc/asound is a directory, so this window must be presenting some distillation of its files' contents.

I hope to provide more responses to your helpful suggestions tomorrow and into the weekend as time allows.

kirby

---

### Post by lidex on 2010-04-22
Can you post the output of this command please:
```
head -n 1 /proc/asound/card*/codec#*
```
To install pulseaudio volume control:
```
sudo apt-get install pavucontrol
```
Go here and do 'Part A':
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by KirbySmith on 2010-04-22
Grabbing a few minutes...

```
 
kirby@THE-SMITHS:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
kirby@THE-SMITHS:~$
 
```I can confirm that with show hidden files checked, filesystem/proc does not show a next level directory /asound.

(I get the same result following sudo.)

installing pulse audio volume control proceeded (terminal-wise) without any alarms.

Pulseaudio volume control is now in Applications

This GUI closely resembles that which opens via System/Preferences/Sound.  All volume levels are at levels of 77% or higher.

The head command still produces the result shown above.

Part A and the other remaining activities will have to wait until probably tomorrow when I will have more time.  Employment calls.  Thanks for the help and your patience.

kirby
ubuntu 9.10

---

### Post by KirbySmith on 2010-04-23
Well, something seems to have become non-functional.  I performed the tasks defined for the Alsa Upgrade Script.  This was an impressively large operation, which upon completion, the noise test worked, video file playback worked, but no sound from line-in was present.  Also, for reasons still unclear, 

cat /proc/asound/version

worked before the upgrade, but 'file not found' resulted after the upgrade.

Next, I tried the Part A tasks.  There were no strange complaints, but now none of the usual sound preference GUIs work.

I intend to redo the upgrade to see if I can fix whatever went wrong.  Perhaps Part A does not assume that Alsa has been upgraded.

kirby

---

### Post by KirbySmith on 2010-04-23
Reinstalling Alsa Upgrade seems to have recovered the relevant GUIs.  Alsa Mixer GUI (the gray one from the menu, not the terminal version) now has the full gamut of controls that the terminal version has.  Playing with it does not lead to any line-in sound.

I  have a lot more options in the Applications/Sound & Video menu, some seemingly spurious.  There one for for Echoaudio soundcards, one for Envy24 soundcards, two for RME soundcards and two for Hammerfall HDSP and DSP.   I suspect I could remove these.

There is one for Pulse Audio Device Chooser that doesn't load any GUI.  xxx Correction: an icon for it appears in the top right icon area.  It doesn't seem to be relevant to my line-in issue.

Starting back at square 1 in a sense, but with Alsa upgraded....

aplay -l reports the same as in my first post.

alsactl -v reports: alsactl version 1.0.22 as expected from the upgrade.

The directory proc/asound now exists.

I haven't found asound.state to look at its content.

The command

```
 
kirby@THE-SMITHS:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory 
```behaves the same as before, but if one looks inside proc/asound one finds card0/codec97#0 and there is subsidiary content if I need to report it.

kirby

---

### Post by lidex on 2010-04-23
OK. What is it? Try this instead:
```
head -n 1 /proc/asound/card*/codec97#*
```

---

### Post by KirbySmith on 2010-04-24
```

kirby@THE-SMITHS:~$ head -n 1 /proc/asound/card*/codec97#*
head: error reading `/proc/asound/card0/codec97#0': Is a directory
kirby@THE-SMITHS:~$ 

```This directory contains two text files.

ac97#0-0 contains

```

0-0/0: Realtek ALC850 rev 0

PCI Subsys Vendor: 0x10de
PCI Subsys Device: 0xcb84

Flags: 80020
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic2
ADC/DAC loopback : off
Double rate slots: 7/8
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF DRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF=6/9 SPDIF
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

```ac97#0-0+regs contains a long series of numbers that I'm guessing wouldn't be interesting.

kirby

---

### Post by lidex on 2010-04-24
Can you post this output please:
```
lsmod | grep snd
```

---

### Post by KirbySmith on 2010-04-24
Yes, thank you.  And here it is:

```

snd_intel8x0           30104  2 
snd_ac97_codec        101536  1 snd_intel8x0
ac97_bus                1596  1 snd_ac97_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76512  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2784  0 
snd_seq_oss            29280  0 
snd_seq_midi            6656  0 
snd_rawmidi            22368  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_seq                50992  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21572  2 snd_pcm,snd_seq
snd_seq_device          7240  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61252  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9124  2 snd_intel8x0,snd_pcm

```On a related front, the Alsa-Update tarball includes a file named HD-Audio-Models.txt.  This listing of sound models does not include the Realtek Karajan ALC850.  Perhaps my DFI board, purchased in 2006 and possibly designed as far back as 2004, is, Alsa-developer-wise, prehistoric. 

Thanks

kirby

---

### Post by lidex on 2010-04-24
That's OK. It's an AC'97 codec and the alsa module for it is  snd_intel8x0. So we can pass the options for that codec thru alsa-base.conf
```
Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, 6300ESB, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

```

---

### Post by KirbySmith on 2010-04-24
:confused:

lidex:

Was I supposed to add that code or a quantified version of it, or was it presented to illustrate why I need not worry?

Anyway, relative to the result of

lsmod | grep snd

did you see any clues that would explain Line-in silence?

Continued thanks

kirby

---

### Post by uMany on 2010-04-24
Hi,
I have the same problem here in my Vaio, no input sound. I've been looking for a solution to this from 3 weeks now.
Hope you can find it an post it

---

### Post by lidex on 2010-04-24
> **KirbySmith said:**
> :confused:

lidex:

Was I supposed to add that code or a quantified version of it, or was it presented to illustrate why I need not worry?

Anyway, relative to the result of

lsmod | grep snd

did you see any clues that would explain Line-in silence?

Continued thanks

kirby

Yes :)
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by lidex on 2010-04-24
> **uMany said:**
> Hi,
I have the same problem here in my Vaio, no input sound. I've been looking for a solution to this from 3 weeks now.
Hope you can find it an post it
Unrelated hardware. Start your own thread and PM me the url. I'll see what I can do.

---

### Post by KirbySmith on 2010-04-25
Thanks again lidex

OK, did those things.  F6 showed "default" was lit, but I changed it to "nVidia."  No effect on null output from line-in.  Alsamixer controls otherwise look the same to me as before, both play and capture.  Video file playback remained normal.

System>Preferences>Sound looks like a candidate for attention.  First, there is no specific hardware listed.  That is, nVidia doesn't appear anywhere.  The hardware tab has generic listings, starting with "off" and ending with "analog stereo duplex."  This is a bit concerning by itself.

If the generic listing is what you meant, then perhaps there is a cockpit error here, as I have assumed that "analog stereo duplex" would best describe the input/output relationship of the line-in connection.  Maybe some other generic description such as "analog surround 4.1 output" would be correct.  (Not that I've managed to get any of these to work on line-in.)  However, many of them when selected either have no video playback sound or the sound is jerky.

kirby

---

### Post by KirbySmith on 2010-04-26
Maybe the more efficient approach is to resist the on-going urge to make something that should work, work, and get a video capture card.  The proprietary nVidia Linux driver software I need for my 7800 doesn't seem to have video capability, (or at least I can't find an interface to it) and a single-purpose card would seem to solve both the line-in audio problem and apparent lack of video-in problem.

Wading through the thicket of cards and supported software will be a challenge.

Anyway, lidex, unless you have another idea for me to try, I'll just putter around with the sound as I learn more.  I thank you for all your time that you spent helping.  At least I got an upgraded Alsa out of it, and experience.

kirby

---

