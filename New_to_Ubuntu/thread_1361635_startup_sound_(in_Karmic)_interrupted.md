---
title: "startup sound (in Karmic) interrupted"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by virtual reality on 2009-12-22
Hi there,

upon startup, the startup sound / music (in Karmic Koala) is slightly distorted / interrupted / stuttering / etc.

My laptop is a 5 - 6 year old venerable IBM Thinkpad R50 (albeit with an upgraded HDD and 2GB RAM).

I was reading a bit here and there about pulseaudio, tried to install libsdl1.2debian-pulseaudio (which is supposed to uninstall the alsa equivalent) - this seemed to have worked but with no positive effect, there are multiple programs in the Ubuntu Software Center which can be installed containing pulseaudio in their name, but in short I am lost:

I don't know what and how much of pulseaudio is already installed, how much would be useful to still install, or whether editing the /etc/pulse/daemon.conf file would do any good.

Here is what that file contains:

```
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
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10
```What the h*** does "daemonize" mean? Where is the foolproof how-to / read-me file? Is it an issue of limited CPU, or is it merely buggy software? This is all so confusing...

Skype is working, an audio CD was playing fine; the only problem / slight annoyance: the startup music is stuttering (upon every startup).

Any guidance v much appreciated!

vr.

---

### Post by yeats on 2009-12-22
I have the same issue on one of my computers and I don't know the solution, but "daemonize" means to cause PulseAudio to run as a daemon program, which is a program that constantly runs in "listening" mode, waiting for you to give it something to do.  MySQL and Apache (and probably anything with a ".d" on the end) are examples of daemons.

> Where is the foolproof how-to / read-me file?

This is where Linux/Open Source is different than proprietary programs - there is not going to be one in the way you expect.  The best way to learn this is by searching these forums and the web for "pulseaudio configuration" and similar search hooks.

---

### Post by virtual reality on 2009-12-23
I don't even know if it has necessarily to do with pulseaudio, so googling pulseaudio might lead to a long road down the wrong track...  The issue remains, on every startup.  Is this issue worthy of filing a bug? Is it a bug (I would think so)?  Anyone else with the same symptom? Any solutions found yet?  ~.~.~  If it were a pulseaudio issue I might try resample-method &quot;trivial&quot;, see for instance [http://wiki.ubuntuusers.de/PulseAudio](http://wiki.ubuntuusers.de/PulseAudio) (German) - but I am reluctant to do so because I don't have any sound problems other than at startup (at least I haven't noticed) - so I wouldn't want to compromise the sound quality of skype or other music playback only to get a crisp startup melody...  vr.

---

### Post by madnessjack on 2009-12-23
I've got exactly the same problem. The audio skips and the graphic animation jerks. Everything else is fine. Maybe too much going on during log-on for the PC to handle sound as well?

---

### Post by audiomick on 2009-12-23
Hallo.
My startup sound was pretty crappy after a fresh install, I think 9.04, and my computer is reasonably fast (dual core @3.3 GHz ) and has 4GB RAM.
I don't know what it is like now, as I turned the sound off. My computer isn't allowed to make noises...:)

---

### Post by llawwehttam on 2009-12-23
This problem sounds like its caused by audio drivers. Make sure there up to date.

---

### Post by virtual reality on 2009-12-23
{ system > administration > update manager } states that everything is up to date.

Need I look elsewhere, e.g.

 - synaptic package manager

or

 - ubuntu software center ?

Or, could it be that there just ain't no bugfix-update available for this - apparent - bug as yet ?

vr.

---

### Post by virtual reality on 2009-12-29
No-one else got any ideas? Not that it's soooooo important. Would be nice, that's all.

vr.

---

### Post by KiwiPete on 2010-01-02
I have the same problem. All sound works fine except that during the startup there is a stuttering in the startup sound. Has anyone out there managed to solve this small problem?
KiwiPete

---

### Post by tom.swartz07 on 2010-01-02
> **madnessjack said:**
> I've got exactly the same problem. The audio skips and the graphic animation jerks. Everything else is fine. Maybe too much going on during log-on for the PC to handle sound as well?

My second laptop does the same thing. I would put money on the idea that the CPU is just maxing out during logon and pushes the sounds to the bottom of the priority queue.

---

### Post by virtual reality on 2010-01-03
priority (for me and I guess most of us) is quick startup.

but wouldn't it be nice if the startup tune only started to play after startup is 99 or even 100 % complete and when even an old(er) CPU can handle it smoothly?

vr.

---

