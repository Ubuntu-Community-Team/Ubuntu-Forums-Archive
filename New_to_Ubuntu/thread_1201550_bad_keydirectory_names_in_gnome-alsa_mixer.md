---
title: "bad key/directory names in gnome-alsa mixer"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by tpgames on 2009-07-01
Reconfiguring the gnome-alsa file  using 
```
cd /usr/share/alsa/ && gedit alsa.conf
```
 did not give me anything that allowed me how to fix the below errors:
```

Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Master_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names

```

Any help is greatly appreciated. Uninstalling and reinstalling did not work. None of the tutorials I've found has worked. Thanks! 

ps. I started new thread as other thread asked a specific question that was answered.

---

### Post by LowSky on 2009-07-01
try

sudo gedit /usr/share/alsa/alsa.conf

---

### Post by tpgames on 2009-07-01
> **LowSky said:**
> try

sudo gedit /usr/share/alsa/alsa.conf


Please read all of this. I hope I've finally made myself clear. I need a solution to the error message I posted earlier in this thread. Thanks in advance!
 
What I am asking for is a silly:mad:  solution to get rid of that stupid error that insist on miss-naming the files and adding the stupid "," where there isn't supposed to be one. And why am I even getting this error in the first place when I redid the entire tutorial of installing pulse, etc. And unsintall and reinstall gnome-alsa and purged EVERYTHING.  I thought it would auto put thing and label things correctly.  I want a solution to the error.

This will NOT work as a search in that file for "," or "SigmaTelSTAC9708,11-Master" gave me "phrase not found".  Which is why I posted a new thread with a new question which unfortunately was misunderstood. I thank you for your solution as it might come in handy later. 

Thanks!

---

### Post by LowSky on 2009-07-01
ok I did some sluething around on google. SigmaTel_STAC9708, which is your audio chipset has some issues... should work fine in the newer version of Ubuntu 9.04, as this [LINK]("link https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/106903") says. I'm assuming you on 8.04 as your profile says...

You can also try to install this package if you dont want to upgrade, but it might not work as it has dependences, below is the link to the file. It will easily install as its a Deb file.
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb)


Sorry no one has been helping you with this issue, please be aware that people are volunteering their time, and for the most part, most poeple here are novices who have learned most of the simple commands and fixes. Sure some people are experienced and can help but they are few and far inbetween, if you cant find a soluitons try using Launchpad, sometimes you get more experienced users there

---

### Post by tpgames on 2009-07-01
Thank you! That is what I missed when I googled.  Question though: Could the following problem  be all related to 8.04 and the chipset? If so, I'll just upgrade. 

The problem:
2) How do I resolve the sound issues, now that I finally got the system recognized on the tab and get the system beep errors but testing sound under preferences/sound nets me no sound? (I did use Rhythm box before to test for sound).

The lack of help issue:  This is why I hope that someday, I might be able to join in on the helping. 

I'm going to post this here in case it is useful for solving all of my sound issues. If not, I'll wait until the CD gets here and do a fresh install of Jaunty as I think I have several issues going on. 


Here's is what I get now PLUS the gnome-alsa mixer configuration error: (EDIT may be chipset as suggested by LowSky)
The application **does not** play audio IN applications And when I test sound in System but does give me system beep errors within applications but **does** list an entry in the Playback tab; (This is even after uninstall gnome-alsa mixer and LEAVING it uninstalled).
 [COLOR=Blue]- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.[/COLOR]

Here is the information that the how-to requests that I post:
1) I did edit the source list a second time. I am using 8.04, amd but I believe its a 32-bit as computer is older. 
2) This is with the Radio Rhythm box on as I forgot to turn it off first:
```
 jyzrxal@jyzrxal-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
```3) ```
 jyzrxal@jyzrxal-desktop:~$  pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
OIL: ERROR liboiltest.c 361: oil_test_check_impl(): illegal instruction in mmxCombineAddU
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 44099 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=@DEFAULT_SOURCE@ loop=0' due to GConf configuration.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: source-output.c: Created output 0 "RTP Monitor Stream" on alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0 with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46132, SSRC=0xae41302a, payload=10, initial sequence #14670
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=jyzrxal 3455043696 0 IN IP4 192.168.2.7
I: module-rtp-send.c: s=PulseAudio RTP Stream on jyzrxal-desktop
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3455043696 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46132 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #5; argument: "source=@DEFAULT_SOURCE@ loop=0").
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA" on alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-combine" (index: #6; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #7; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args '' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args '' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #9; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #12; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'.
I: module-default-device-restore.c: Manually configured default source, not overwriting.
I: module.c: Loaded "module-default-device-restore" (index: #13; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #14; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #16; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...

```Then it keeps repeating the last line over and over again.  

This is with Rhythm box and everything audio closed:
```

jyzrxal@jyzrxal-desktop:~$  pkill pulseaudio; sleep 2; pulseaudio -v
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
OIL: ERROR liboiltest.c 361: oil_test_check_impl(): illegal instruction in mmxCombineAddU
I: module-hal-detect.c: Trying capability alsa
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0").
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 44099 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: source-output.c: Created output 0 "RTP Monitor Stream" on alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0 with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46626, SSRC=0x1a687df3, payload=10, initial sequence #28922
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=jyzrxal 3455044867 0 IN IP4 192.168.2.7
I: module-rtp-send.c: s=PulseAudio RTP Stream on jyzrxal-desktop
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3455044867 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46626 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #5; argument: "source=@DEFAULT_SOURCE@ loop=0").
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA" on alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
I: module.c: Loaded "module-combine" (index: #6; argument: "").
I: module.c: Loaded "module-rtp-recv" (index: #7; argument: "").
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #8; argument: "").
I: module.c: Loaded "module-esound-protocol-tcp" (index: #9; argument: "").
I: module.c: Loaded "module-zeroconf-discover" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #12; argument: "").
I: module-default-device-restore.c: Manually configured default source, not overwriting.
I: module.c: Loaded "module-default-device-restore" (index: #13; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #14; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #16; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```Then it hangs here. 

EDIT gnome-alsa mixer error maybe Chipset error as posted by LowSky : So 1)  How do I reconfigure the gnome-alsa mixer configurations so that I don't get this...
```
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory 

```


Thanks!  :D

---

### Post by LowSky on 2009-07-01
I included a link to the newest verison of alsamixer.... use the link or upgrade to 9.04

---

### Post by tpgames on 2009-07-01
I'm going to upgrade to Jaunty because the dependencies is part of the issue. 
Thanks! 
I'll consider this thread closed now. :D

(Update: Upgrade didn't work initially, but still need to go through the how-to for tweaks. I will have my sister help me with that tomorrow.)

---

### Post by tpgames on 2009-07-11
The fix: Changing all outputs areas so that only Master is available. 
Under Volume Control --> Changed Device to "Playback: Simultaneous output..."
Under System --> Preferences --> Sound: I changed "Default Mixer Tracks" to Playback: Simultaneous output..."
Result: Only "Master" is available for devices to control, but I get sound. 

My sound is crackly, but I've not gone back to the forum post that mentions the fix for that yet. 

Upgrading to 9.04 didn't work on its own. However, someone gave me a link to another post with the same issues, but I lost that link (and the link to the original post). My computer froze before I could bookmark it. 
Thanks! I hope this helps someone. :D

---

### Post by smoothshifter on 2012-11-07
This error drove me a little nutty too. Apparently it has been reported  for a few years now, I saw on one post. I have induced that it is simply  a bug in the program code itself. I am no linux poweruser, but I have  found a workaround... not a fix.

I chose to use the terminal  version, alsamixer, in place of the desktop version. I created a  shortcut on the panel and used the pulse volume icon for the launcher.  If you do this and use keyboard shortcuts for volume operation, they  will not work without creating a custom command. 
I should also add that I use Ubuntu 11.10

Here are my idiot proof instructions for this simple procedure:

-hold alt + right-click on the panel you want the shortcut on and choose "Add to Panel".
-choose "Custom Application Launcher" and click add.
-Type = "Application in Terminal"
-Name = Alsa Mixer or whatever you choose
-Command = alsamixer
-click on the icon selection button (top left) and choose multimedia-volume-control.svg or another icon of your choice.
-click "Open" and hit "OK"

now for the keyboard shortcuts for volume control...

-Go to system settings... for me it is Applications, System Tools, System Settings
-choose Keyboard (not Keyboard Layout), then shortcuts
-choose Custom Shortcuts and click the "+" down bottom
-
-choose a name like volume up, volume down or mute and add the appropriate command without quotes (listed below).
-----vol up               = " amixer -c 0 -- sset Master playback 1+ unmute "
-----vol down         = " amixer -c 0 -- sset Master playback 1- unmute "
-----mute/unmute = " amixer sset Master toggle "
-click "disabled" on the right side of each entry that you added to input the new key bindings (ctrl + left/right/down, etc.)

Now  test your settings to make sure all is working well. If so, you're  done. If there is a mistake in the command... click the command to edit  (left side).
I know that pulse volume control is a gui option as  opposed to alsamixer, but I prefer to have all inputs/outputs on one  screen if possible.
   One thing that I am missing now though, is the  volume animation/sound which used to come on while using the keyboard  volume controls. If someone knows how I can get them back, I would  appreciate it. If not, it's no great loss anyway.

:guitar:

---

### Post by wildmanne39 on 2012-11-07
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

