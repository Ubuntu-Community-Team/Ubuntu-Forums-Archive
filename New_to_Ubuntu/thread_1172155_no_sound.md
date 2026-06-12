---
title: "no sound"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by jj3502 on 2009-05-28
(ubuntu 9.04)
i cant play any sound 

the only sound i get is "beep"

---

### Post by s.fox on 2009-05-28
Hi,

Check sound card

```

aplay -l 

```
```

pkill pulseaudio; sleep 2; pulseaudio -vv 

```
Check mixer

     ```

 alsamixer -Dhw 

```

Ref:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

-Ash R

---

### Post by jj3502 on 2009-05-28
Heres the output


```
jeremy@jeremy-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```





```


jeremy@jeremy-desktop:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 75f01f8cff3bcce923d5e5474a1ed65b.
I: main.c: Using runtime directory /home/jeremy/.pulse/75f01f8cff3bcce923d5e5474a1ed65b:runtime.
I: main.c: Using state directory /home/jeremy/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/jeremy/.pulse/75f01f8cff3bcce923d5e5474a1ed65b:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/jeremy/.pulse/75f01f8cff3bcce923d5e5474a1ed65b:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "PCM".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Mixer doesn't support dB information.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale not supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'C-Media CMI8738' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1849688064
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1849688064
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=1 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "Mic".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 7.
I: module-alsa-source.c: Mixer doesn't support dB information.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale not supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'C-Media CMI8738' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1849688064
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1849688064
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=1 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_3a3e_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_3a3e_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_3a3e_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 1 "alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 2 "alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thre
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #6; argument: "device_id=0 sink_name=alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0.
I: source.c: Created source 3 "alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 31.
I: module-alsa-source.c: Volume ranges from -16.50 dB to 30.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thresh
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
D: module-alsa-source.c: Requested volume: 0:  22% 1:  22%
D: module-alsa-source.c: Got hardware volume: 0:  25% 1:  25%
D: module-alsa-source.c: Calculated software volume: 0:  97% 1:  97%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #7; argument: "device_id=0 source_name=alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_3a3e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #8; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #9; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #10; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...

^CE: module-gconf.c: Unable to read or parse data from client.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
I: module.c: Unloading "module-alsa-sink" (index: #4).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #5).
I: module.c: Unloading "module-alsa-sink" (index: #6).
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 2 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 4 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-null-sink" (index: #16; argument: "sink_name=auto_null").
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 2 "alsa_output.pci_8086_3a3e_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #6).
I: module.c: Unloading "module-alsa-source" (index: #7).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 3 "alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #7).
I: module.c: Unloading "module-hal-detect" (index: #8).
I: module.c: Unloaded "module-hal-detect" (index: #8).
I: module.c: Unloading "module-esound-protocol-unix" (index: #9).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #9).
I: module.c: Unloading "module-native-protocol-unix" (index: #10).
I: module.c: Unloaded "module-native-protocol-unix" (index: #10).
I: module.c: Unloading "module-default-device-restore" (index: #11).
I: module.c: Unloaded "module-default-device-restore" (index: #11).
I: module.c: Unloading "module-rescue-streams" (index: #12).
I: module.c: Unloaded "module-rescue-streams" (index: #12).
I: module.c: Unloading "module-always-sink" (index: #13).
I: module.c: Unloaded "module-always-sink" (index: #13).
I: module.c: Unloading "module-console-kit" (index: #14).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Unloaded "module-console-kit" (index: #14).
I: module.c: Unloading "module-position-event-sounds" (index: #15).
I: module.c: Unloaded "module-position-event-sounds" (index: #15).
I: module.c: Unloading "module-null-sink" (index: #16).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 2 "auto_null"
I: source.c: Freeing source 4 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #16).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.
jeremy@jeremy-desktop:~$ 
```

---

### Post by propagation_of_sound on 2009-05-28
Which sound card do you want to use?
Which interface-driver do you want to use? ALSA/PulseAudio etc...
Is the beep coming from your speakers or is it the system beep (coming from your motherboard)

-j

---

### Post by jj3502 on 2009-05-28
oh... i also have windows and there is onbord sound for most audio and a card for FSX voice com. (my motherboard is a asus p5q se and i what the sound to come thru that (card 0 i think))

---

### Post by jj3502 on 2009-05-29
found more info i can here feint sound with loads of interference when i turn the sound up _**very**_ loud

---

### Post by jj3502 on 2009-05-29
"beep" comes clearly thru card 0 speakers! and the music is ogg and mp3 but i downloaded the ubuntu-restricted-extras

---

### Post by ParanoidMetroid on 2009-05-29
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

Check and see if that link helps.  I got my sound issues resolved thanks to that.

---

### Post by jj3502 on 2009-05-29
nope still can't get it to work the only sound that comes from my speakers is "BEEP"

---

### Post by jj3502 on 2009-05-29
I Fixed it!!! AND don't know how i did it!!! :p:p:p:p:p:p:p

---

