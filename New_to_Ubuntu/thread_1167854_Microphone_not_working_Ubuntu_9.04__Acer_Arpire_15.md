---
title: "Microphone not working Ubuntu 9.04 / Acer Arpire 150"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by tomreid on 2009-05-23
Hi
 I got the above Acer notebook yesterday and find everything seems to work fine with the version of Ububtu (9.04) I installed, except the microphone.
 There are a number of options that the set up panel in Skype allow you to select in it's "Sound Devices" section and every other option apart from "HDA Intel (HW, Intel, 0) results in the Skype Test Call coming back with the error message "Problem with Audio Capture". Funnily enough today I tried to set "Pulse" as my input device and skype didn't come back with the "Problem with Audio Capture" error message, but it didn't work anyway.
 
When I run the test call in Skype it acts like it should work (e.g. the Skype test call does not return an error message) but when the Skype test call tries to play back the recording of my voice I made, all I hear is hiss.
 I've tried numerous other fixes suggested by other questions and answers I found here and by Googling (I'm trying to avoid some of the more drastic solutions I found, like replacing pulse audio).
 
I know the built in Mic works on the Acer, as I left Windows on the machine and Skype works fine on Windows, I hear my voice no problem.
 I've also tried all the obvious things, like right clicking on the volume control in Gnome, selecting "open volume control" and making sure no input devices are muted. I've also tried the "mic boost" setting and that results in the audio in the Acer producing a lot of hiss.
 
All this makes me think that the problem is that the audio software in Ubunto is just not recognising the Mic. If there is a way to specify which audio input device that Ubunbtu should recognise, then I can't find it.
 
Oh and I tried recording my voice using "sound recorder" but no joy there either.
 One of the help posts I saw asked the person with the question to run a command in Amixer and report the results. I ran this command in my machine and here are the results:
 
om@tom-acer:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 52 [81%] [-12.00dB] [on]
  Front Right: Playback 52 [81%] [-12.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%]
  Front Right: 1 [33%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic'
  Item0: 'Front Mic'
 Please can someone help, seems a shame to have to keep Windows on this machine for just skype.
 cheers
 Tom.

---

### Post by guushoekman on 2009-09-26
I have an Acer Aspire 4376 and the same problem. 
Does anyone have a solution?

---

### Post by Nittalope on 2009-12-27
I've got the same problem on Aspire 6530G with Ubuntu 9.10. There is already a bug #478867 in Launchpad. Still hoping somebody could fix it.

 amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 13 [42%] [-27.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 251 [98%] [0.80dB]
  Front Right: Playback 251 [98%] [0.80dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 16 [52%] [7.50dB] [on]
  Front Right: Capture 16 [52%] [7.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Ext Mic' 'Line In' 'CD' 'Input Mix' 'Int Mic'
  Item0: 'Int Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Ext Mic' 'Line In' 'CD' 'Input Mix'
  Item0: 'Ext Mic'

---

