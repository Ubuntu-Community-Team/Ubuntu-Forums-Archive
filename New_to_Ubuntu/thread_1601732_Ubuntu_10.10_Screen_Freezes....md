---
title: "Ubuntu 10.10 Screen Freezes..."
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Billisnice on 2010-10-20
Every 10-15 minutes my system freezes and i have to wait a few seconds for it to come back.  The internet freezes too. I noticed if I have sound playing before if freezes it does not affect sound, it keeps on going non stop like youtuve. But the screen in non responsive. 

I never had an issue with any of the other release since ver 6...

---

### Post by SpinningAround on 2010-10-20
Wild guess, but are you using an ATI graphic card? Might be that ATI have dropped support for it, if X server version was changed in 10.10.

---

### Post by Billisnice on 2010-10-20
I am not sure if ATI or not. I have NVIDIA drivers installed. AMD Athlon 64 x 2 dual processors  4000+

---

### Post by mick8985 on 2010-10-20
open up a terminal and type
```
lspci
```
post the results here
Do the same for 
```
lsmod
```

---

### Post by SpinningAround on 2010-10-20
> **Billisnice said:**
> I am not sure if ATI or not. I have NVIDIA drivers installed. AMD Athlon 64 x 2 dual processors  4000+

Most likely is Nvida then, try in terminal what it shows.
```
lspci | grep VGA
```

I know two issues that cause total freeze, ATI cards that isn't supported and a laptop that is running on battery power. The later might be a quite unique problem.

I have you tried uninstalling Nvidia's graphic drivers? (System>Administration>Hardware Drivers)

---

### Post by Billisnice on 2010-10-20
bn@bn-desktop:~$ sudo lspci
[sudo] password for bn: 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
bn@bn-desktop:~$ 



bn@bn-desktop:~$ lsmod
Module                  Size  Used by
r8192s_usb            287340  0 
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
arc4                    1165  0 
rt73usb                22442  0 
crc_itu_t               1383  1 rt73usb
rt2500usb              18049  0 
rt2x00usb               9779  2 rt73usb,rt2500usb
rt2x00lib              27275  3 rt73usb,rt2500usb,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              231541  2 rt2x00usb,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
binfmt_misc             6599  1 
nvidia               9329739  52 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
usblp                  10651  0 
parport_pc             26058  1 
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
agpgart                32011  1 nvidia
k8temp                  3132  0 
eeprom_93cx6            1345  1 r8192s_usb
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
floppy                 54311  0 
forcedeth              49433  0 
sata_nv                19420  2 
pata_amd                8746  0 
bn@bn-desktop:~$

---

### Post by Billisnice on 2010-10-20
I tried twice...

bn@bn-desktop:~$ sudo lspci | grep VGA
\00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)

bn@bn-desktop:~$ lspci | grep VGA
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
bn@bn-desktop:~$

---

### Post by mick8985 on 2010-10-20
You're definitely running an nvidia card and using the proprietary nvidia drivers.
I suspect though that you're problem might not be video related at all.
When your screen freezes what actually happens? do all your windows grey out?
You might experience something like this if you don't have a lot of ram and your memory usage goes over your capacity and you force you're system to start swapping.

---

### Post by Billisnice on 2010-10-20
My screen does not gray out. It is normal colors, etc.  I can move the mouse normally too.

My sound is not affected. I can  hear the sound of youtube or hulu going ok, but the screen freezes and comes back.

Can you tell what type of memory i have so if i buy some i will know.

---

### Post by mick8985 on 2010-10-20
I'm not sure for definite that ram is your problem, but i have noticed in recent releases that the memory usage has skyrocketed and I'd advise at least 2 gigs of ram to run ubuntu, or turn a lot of things off.
But you can find all the info about your ram using
```
cat /proc/meminfo
```
You can also see your total ram and current ram usage in System Monitor. (System>Administration>System Monitor)

If your swap usage seems high and your memory usage is over 80% might be time to invest in some more RAM.

Edit:
Didn't read your question properly, as per which ram you need to buy, I'm not sure if there is a command for finding out what kind of ram you are using, the best bet is to open up your pc and have a look. Chances are it's ddr2.

---

### Post by jtarin on 2010-10-20
Your mouse movement is normal but will not interact with any screen elements? Are you able to interact with the keyboard? Next time it freezes see if you can close the topmost window with Alt + F4 to check keyboard interaction.

---

### Post by badchoice on 2010-10-21
I have the same problem, but mine doesn't come back...

I can move the mouse but nothing else works, no key combitaion, anything..

---

### Post by freddybob on 2010-10-24
> **badchoice said:**
> I have the same problem, but mine doesn't come back...

I can move the mouse but nothing else works, no key combitaion, anything..

I have the same problem and have to hold the power button for 5 seconds to reset the machine.

It happens whenever I watch a video (or even listen to music with visualisation) in Totem or VLC.

Disabling the nvidia driver (System > Administration > Additional Drivers) fixes the problem.  But this of course means I am then using the nouveau driver which introduces another bug where no video signal is sent to my screen while booting (and so I have to edit the grub line to add 'nomodeset').

*Ubuntu 10.10 64bit / Nvidia GeForce 210*

**Edit:** I solved my GPU freezing problem by installing *32bit* Ubuntu.

---

### Post by yafes on 2010-10-31
It's same problem.

I changed the Power Management options for solving that.

I think, this is a "display sleep" problem. When display goes sleep, it can't be turn back.

You can change the "Sleep display" option to "never" in "On AC Power" and "On Battery Power" tabset in *Power Management Preferences (System/Preferences)*.

Good luck...
-y

---

