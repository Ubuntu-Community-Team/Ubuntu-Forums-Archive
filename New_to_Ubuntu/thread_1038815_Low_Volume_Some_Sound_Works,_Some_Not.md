---
title: "Low Volume Some Sound Works, Some Not"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by ~zoey~ on 2009-01-13
My integrated sound is recognized;
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Device 4001
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 90420000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
The sound preference window testing gives a tone for every thing but for  Audio Conferencing, sound capture does not work.
Volume is set high in Volume Control, Alsa Mixer and Pulse Audio, but it is extremely low in the sounds that work (Rhythmbox & login).
I am running Ubuntu 8.10.  I have never had this problem before...where I sort of have sound, but not really.  I would appreciate some suggestions.

Thanks, zoey

---

### Post by kansasnoob on 2009-01-13
Start by installing gnome-alsamixer from synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Look at mine for comparison:

[ATTACH]99716[/ATTACH]

[ATTACH]99717[/ATTACH]

---

### Post by ~zoey~ on 2009-01-13
My Volume is set at high in Gnome Alsa Mixer, volume control and Pulse Audio.

Thanks, zoey

---

### Post by ~zoey~ on 2009-01-14
More information; ubuntu 8.10 is on a Sata drive using an Intel DG33TL board with onboard sound. The sound has been faint or non-existent since installation. In sound preferences everything yields a tone except sound capture. I have the volume set high in master volume control, gnome alsa mixer and pulse audio. I have very faint login sounds and Rhythm Box will play softly with volume on high. I attempted a fix for pulse audio as posted here; [http://ubuntuforums.org/showthread.p...ighlight=sound](http://ubuntuforums.org/showthread.p...ighlight=sound) but bash didn't like the very first command. My onboard sound is recognized;
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

Here is the output for pulse audio;
margo@margo-desktop:~$ sudo pkill pulseaudio; sleep 2; pulseaudio -vv
[sudo] password for margo:
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
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: No previous default sink setting, ignoring.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-hal-detect" (index: #2).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #2).
I: module.c: Unloading "module-esound-protocol-unix" (index: #3).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #3).
I: module.c: Unloading "module-native-protocol-unix" (index: #4).
I: module.c: Unloaded "module-native-protocol-unix" (index: #4).
I: module.c: Unloading "module-gconf" (index: #5).
I: module.c: Unloaded "module-gconf" (index: #5).
I: module.c: Unloading "module-volume-restore" (index: #6).
I: module.c: Unloaded "module-volume-restore" (index: #6).
I: module.c: Unloading "module-default-device-restore" (index: #7).
I: module.c: Unloaded "module-default-device-restore" (index: #7).
I: module.c: Unloading "module-rescue-streams" (index: #8).
I: module.c: Unloaded "module-rescue-streams" (index: #8).
I: module.c: Unloading "module-suspend-on-idle" (index: #9).
I: module.c: Unloaded "module-suspend-on-idle" (index: #9).
I: module.c: Unloading "module-x11-publish" (index: #10).
I: module.c: Unloaded "module-x11-publish" (index: #10).
I: main.c: Daemon terminated.
I checked permissions in users and groups and pulse, pulse access and pulse-rt are all listed.
Does this tell anyone anything? I haven't a clue and I would really appreciate some help in getting my sound going.
Thanks, zoey

---

