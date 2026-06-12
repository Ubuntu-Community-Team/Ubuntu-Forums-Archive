---
title: "Reinstall Sound Problems"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Tumpster on 2008-12-10
So I updated my Hardy with a fresh one, I was running 8.04 and now wiped my hard drive clean and installed 8.04.1, I've since noticed it now runs on PulseAudio instead of ALSA. My problems are two fold, one is that it only sees 2 speakers, my left and right, when I bring up the Pulse Audio Volume Control under "Output Devices." I have a Logitech 5.1 surround sound setup and get no audio through the other 3 speakers and it's quite frustrating.

Problem two is the fact that Totem and most things are very quiet, music plays at a reasonable volume but I've noticed I'm having to turn up my master pretty high up to get to what is a reasonable volume level. I usually never had to do this during my last install. Any ideas?

Big thanks!

---

### Post by Tumpster on 2008-12-10
Also, when I test this out:
speaker-test -Dplug:surround51 -c6 -l1 -twav

I get response from each speaker.....

---

### Post by Tumpster on 2008-12-11
Help, please?!
I no longer get a response from the speaker test....

Output of my dameon.conf
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)

### Manual config for configuring surround sound. Comment out line below to revert to defaults.
load-module module-alsa-sink device_id=0 channels=6 channel_map= front-left, front-right, front-center, rear-left, rear-right, lfe

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25

---

### Post by clive littlewood on 2008-12-11
Hi

Change to ALSA in the sound settings drop down list.

Is that better ??

Clive

---

### Post by Tumpster on 2008-12-17
Much after I reinstalled ALSA

---

