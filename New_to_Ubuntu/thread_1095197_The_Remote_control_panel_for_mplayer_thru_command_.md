---
title: "The Remote control panel for mplayer thru command term LIRC help"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-13
I am trying to start a dvd  using mplayer ( it is encryped) it plays but it doesnt let the remote control panel come up with it. P.S. I know that I need to set the device but the LIRC is what I am trying to fix.



eric@eric:~$ mplayer dvd://1 -lirc -dvd-device /dev/dvd1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU  230   @ 1.60GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 15 titles on this DVD.
There are 40 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
audio stream: 2 format: ac3 (5.1) language: es aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: fr
subtitle ( sid ): 5 language: es
subtitle ( sid ): 7 language: fr
subtitle ( sid ): 9 language: es
number of subtitles on disk: 5
MPEG-PS file format detected.

---

### Post by ericeclifford on 2009-03-13
is there perhaps a input command I have to put into the line I tried doing -input lirc

Do I have to change a certain config file?

---

