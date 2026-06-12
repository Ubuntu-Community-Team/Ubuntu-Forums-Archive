---
title: "Sound Problem on 8.04"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-04-25
Hi ALL

I'm struggling with my Ubuntu Linux 8.04 LTS with sound problems every 2 minitue I have to restart. Please any one can help me. That would be greatful. If anyone can reply to this I can tell my problem what I'm facing.   

I feel as an LTS if you consider the sound part of UBUNTU 8.04 .It is not been suiting for the word LTS. Because of the problems.

---

### Post by nitstorm on 2010-04-25
<sorry for the wrong info i posted here earlier> Why not upgrade to 10.04 when it releases on April 29, probably will solve the issue, I have had multimedia problems when I was on 9.04 but it got resolved when I upgraded to 9.10

---

### Post by k3lt01 on 2010-04-25
> **nitstorm said:**
> The 8.04 LTS support expires in just a few more days. The new Lucid Lynx 10.04 LTS releases on April 29th. Why not upgrade to it, probably will solve the issue, I have multimedia problems when I was on 9.04 but it got resolved when I upgraded to 9.10That is so not true, Support for 8.04 goes for another 12 months for desktops and 3 more years for servers. Please don't tell people incorrect things if you cannot show where you got your information from.

---

### Post by k3lt01 on 2010-04-25
> **vipin.balakrishnan said:**
> Hi ALL

I'm struggling with my Ubuntu Linux 8.04 LTS with sound problems every 2 minitue I have to restart. Please any one can help me. That would be greatful. If anyone can reply to this I can tell my problem what I'm facing.   

I feel as an LTS if you consider the sound part of UBUNTU 8.04 .It is not been suiting for the word LTS. Because of the problems.Hi vipin, can you give us your computers specifications so we know what hardware we are trying to diagnose.

EDIT: Have you taken a look at [this thread]("http://ubuntuforums.org/showthread.php?t=766683")?

---

### Post by nitstorm on 2010-04-25
> **k3lt01 said:**
> That is so not true, Support for 8.04 goes for another 12 months for desktops and 3 more years for servers. Please don't tell people incorrect things if you cannot show where you got your information from.

Extremely sorry for the wrong info, i have edited my post to show nothing.

---

### Post by Zintha on 2010-04-25
Please don't ask if you can ask a question, just ask the question up front, as now theres a thread going and nobody knows what the sound problem is.

---

### Post by vipin.balakrishnan on 2010-04-25
Hi ALL

 Thanks for replying. 

I'm using Ubuntu 8.04 LTS , Pulseaudio 0.9.10 and kernel 2.6.24-27-generic. When I try to run any movies in my system, after sometime it will give me an error 

pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!. 

After this error pulseaudio throw below error.
[HTML]
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: main.c: Daemon shutdown initiated.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-sink" (index: #0).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No evacuation sink found.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-suspend-on-idle.c: Sink alsa_output.surround40_0 becomes idle.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-suspend-on-idle.c: Sink alsa_output.surround40_0 becomes idle.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: sink-input.c: Freeing output 0 "audio stream"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: sink.c: Freeing sink 0 "alsa_output.surround40_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 0 "alsa_output.surround40_0.monitor"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-sink" (index: #0).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-source" (index: #1).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-source.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 1 "alsa_input.pci_1102_7_sound_card_0_alsa_capture_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-source" (index: #1).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-source" (index: #2).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-source.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 2 "alsa_input.pci_1131_7134_sound_card_0_alsa_capture_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-source" (index: #2).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-hal-detect" (index: #3).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-hal-detect" (index: #3).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-esound-protocol-unix" (index: #4).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 0 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 1 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 4 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 7 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-esound-protocol-unix" (index: #4).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-native-protocol-unix" (index: #5).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 2 "VLC media player"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-native-protocol-unix" (index: #5).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-volume-restore" (index: #6).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-volume-restore" (index: #6).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-default-device-restore" (index: #7).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-default-device-restore" (index: #7).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-rescue-streams" (index: #8).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-rescue-streams" (index: #8).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-suspend-on-idle" (index: #9).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-suspend-on-idle" (index: #9).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-gconf" (index: #10).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-gconf" (index: #10).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-x11-publish" (index: #11).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-x11-publish" (index: #11).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: main.c: Daemon terminated.
[/HTML]

There will not be any sound after this. As soon as when I check in my system monitor pulseaudio service will not be running. Please help me.

I tried to open Pulseaudio device choser.  It is throwing Connection refused error.

Once more thing I noticed is It will keep on throwning error 

**module-alsa-sink.c: EAGAIN**

---

### Post by k3lt01 on 2010-04-25
Vipin, what is your computers hardware?

---

### Post by vipin.balakrishnan on 2010-04-25
Hi ALL 

I have attached one more screenshot here for the same issue. After pulseaudio crash. Exail player shows 1..8 GB is used. This is very strange. Before the pulseaudio crash.Both pulseaudio and exaile player increase there memory utilization every 3 or 4 min. I'm not able to see what time these memory is getting freed.

 
Please check the attachment to see the memeory utilization.

---

### Post by vipin.balakrishnan on 2010-04-25
Hi ALL,

Please tell me If you want anymore information

```

lspci

```

[HTML]
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

[/HTML]

```
  aplay -l

```

[HTML]
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/HTML]

---

### Post by k3lt01 on 2010-04-25
So you have a Creative card, ok that's a start. I have found Creative to work extremely well but then again mine is about 8 years old so the drivers are within the kernel.

Is your system up to date? Have you tried to see if there are any hardware device drivers available through System > Administration > Hardware Drivers?

Have you looked at the thread I linked to in my 2nd post?

---

### Post by vipin.balakrishnan on 2010-04-25
Hi k3lt01,

My system is upto date with all update for Ubuntu 8.04 LTS. When I look into Hardware drivers I'm able to see only Nvida Accelerated Graphics Driver (I have attached the screenshot. 

 **k3lt01** when I run lsmod |grep snd ,There snd modules are also loaded.

```

 lsmod |grep snd

```

[HTML]
snd_ca0106             36192  1 
snd_ac97_codec        101028  1 snd_ca0106
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3072  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm

[/HTML]

---

### Post by k3lt01 on 2010-04-25
Go to System > Administration > System Testing and follow the instructions and tell me what happens.

Also you haven't answered if you have had a look at the multimedia thread I linked for you. It should really be the first place you looks at for this. After you have gone through that then please let us know what is happening.

---

### Post by vipin.balakrishnan on 2010-04-25
Hi k3lt01,

I have gone through the link you send. Just I have doubt on this article, This will only uninstall the mp3 and flash pulgin + alsa-oss  in the system?

My problem is I can able to play the sound. But after sometime pulseaudio is terminating the with an error posted in my previous posts.

Can you please tell me someinformation about the link you provided.

After doing the system testing (Hardware testing) I have uploaded the data in launchpad.net. you can have a look on it. Please find the link below.

**[https://launchpad.net/~vipin-bmenon/+hwdb-submissions](https://launchpad.net/~vipin-bmenon/+hwdb-submissions)**

---

### Post by vipin.balakrishnan on 2010-04-25
Hi k3lt01,

One more thing is my system not contain flash or Gnash components. And it is a fresh installed Ubuntu 8.04 LTS with all updates.

---

### Post by k3lt01 on 2010-04-25
The link helps people setup their systems and troubleshoot any problems they are having.

You say it's a fresh install of 8.04, I was thinking you have had it for a while, it may be easier if you just wait a week and download 10.04.

---

### Post by vipin.balakrishnan on 2010-04-25
Hi k3lt01,

 Today I just reinstall my complete Ubuntu 8.04 LTS due to this Pulseaudio Crash. 

I just want to do it in 8.04 LTS is, Hardy has gone through long journey of LTS support. So it will have more fixes and much more stable than Ubuntu 10.04 LTS now released.

---

### Post by k3lt01 on 2010-04-25
Ok, it seems you haven't done a search and if you have your not telling us what you have tried to do to fix your issue. So take a look at [this]("http://ubuntuforums.org/showthread.php?t=789578"), [this]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html"), and [this]("http://glyph.twistedmatrix.com/2008/09/ultimate-ubuntu-pulseaudio-guide.html"). Each one is a different help so please read them and try the solutions they offer.

---

### Post by vipin.balakrishnan on 2010-04-25
Hi k3lt01,

I already done this **forum link** ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578))  on 19 April 2010. After this change also I'm getting same error I have posted Syslog information in my 7 th post this same discussion.

Today I have Reinstalled my complete Ubuntu 8.04 LTS and updated all the update coming.and not updated the above link. Same issue is following with exaile gave me 1..8GB utilzation. 

The** second Link**([http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)) This also I tried removing the Pulseaudio itself instead install esound for mixing. This is corrupting Ubuntu-desktop package installed.

The third link you are given to me is very new for me ([http://glyph.twistedmatrix.com/2008/09/ultimate-ubuntu-pulseaudio-guide.html](http://glyph.twistedmatrix.com/2008/09/ultimate-ubuntu-pulseaudio-guide.html))
I think this disable the ESD of Pulseaudio. 

[B]Can you please tell me how to enable dmix in ALSA and how can I enable sourround40 on ALSA. So can avoid using Pulseaudio this way.
[/B]

---

