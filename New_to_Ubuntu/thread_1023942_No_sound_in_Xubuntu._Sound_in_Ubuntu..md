---
title: "No sound in Xubuntu. Sound in Ubuntu."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by altonbr on 2008-12-28
I've had Ubuntu installed and running, wiped and upgraded, modified and unmodified for over 3 years now. It has always worked and detected my sound card.

I decided to delete all of my preferences in my /home directory and fresh install Xubuntu. Everything has been going well except that there is no sound whatsoever.

I've played with 'alsamixer' and my master, PCM, etc. etc. are all 80%+

> &#9474; Card: Audigy 2 [SB0350b]                                                     &#9474;
&#9474; Chip: SigmaTel STAC9750,51                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00] 

```
$lspci -vv
05:03.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
	Subsystem: Creative Labs Device 0040
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Region 0: I/O ports at dcb8 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp
```

I've installed gnome-alsamixer, but it seems to be of no help.

What can I do to get sound back?

---

### Post by altonbr on 2008-12-28
More info from [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 [SB0350b]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1 "alsa_input.pci_1102_4_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 2 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module-volume-restore.c: starting with empty ruleset.
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_1102_4_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```

---

