---
title: "Maverick uses 99% resources of my CPU"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by 4chan on 2010-10-19
[URL="http://ubuntuforums.org/showthread.php?t=1599255"]My previous thread about my computer that froze when playing audio and video files.
[/URL]
turn out to be a serious issue with maverick, my computer froze because by default maverick eat 99% of my cpu and almost half of my ram size

please see the screenshots

[ATTACH]172829[/ATTACH] [ATTACH]172830[/ATTACH]

as you can see on the screenshot, i did not running any applications except system monitor

please help..

computer specs: P4 2.4 Ghz 1GB of RAM and Nvidia 7200GS

ps: my maverick installation is up to date.

---

### Post by Hippytaff on 2010-10-19
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776)
 
might be a bug

---

### Post by 4chan on 2010-10-19
> **Hippytaff said:**
> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776)
 
might be a bug

yeah might be, but i assume it has something to do with the new sound menu. because if i play music with Aqualung or VLC it is fine but of course cpu usage is still high.

---

### Post by Hippytaff on 2010-10-19
Might be something to do with xorg (the thing that runs Gnome etc). Has this happened since you installed ubuntu...might be worth backing stuff up and trying to reinstall it, though I can't promise this will fix it :-s

---

### Post by themusicalduck on 2010-10-19
It might be worth looking at the processes list again and ordering the processes by CPU usage rather than memory usage, so you can see what is using the most CPU.

---

### Post by 4chan on 2010-10-19
> **Hippytaff said:**
> Might be something to do with xorg (the thing that runs Gnome etc). Has this happened since you installed ubuntu...might be worth backing stuff up and trying to reinstall it, though I can't promise this will fix it :-s

ahh ok. i'm still new to ubuntu and still learning tho. first ubuntu for me is Lucid and i have no problem at all with Lucid.
also i did reinstalling Maverick twice and yeah i still have the same issue.

---

### Post by 4chan on 2010-10-19
> **themusicalduck said:**
> It might be worth looking at the processes list again and ordering the processes by CPU usage rather than memory usage, so you can see what is using the most CPU.

looks like something wrong with Pulse Audio
[ATTACH]172833[/ATTACH]

---

### Post by Elfy on 2010-10-19
I would also look at top in a terminal - I'm not sure about the system monitor as default - tends to always be system monitor at the top ;)

Open a terminal - apps - accessories to look at top 

```
top
shift +f
k
enter
```will ensure it is sorting by CPU

---

### Post by Hippytaff on 2010-10-19
I'm still newish too, but I did a search and looks like there is a bug to do with xorg...might be worth reverting to lucid until its fixed - looks like your using KDE rather than GDM (Gnome) anyway!?, but xorg still runs whatever window display manager you use.
 
Also it might be worth doing what themusicalduck suggested, I might be barking up the wrong tree and a different process might be eating up the cpu!?
 
in the terminal (CTRL+ALT+T to open terminal)
```

top

```
 
will list the processess and what they're using

---

### Post by 4chan on 2010-10-19
> **forestpiskie said:**
> I would also look at top in a terminal - I'm not sure about the system monitor as default - tends to always be system monitor at the top ;)

Open a terminal - apps - accessories to look at top 

```
top
shift +f
k
enter
```will ensure it is sorting by CPU

ok ;)
here you go: [ATTACH]172834[/ATTACH]

---

### Post by Hippytaff on 2010-10-19
> **forestpiskie said:**
> I would also look at top in a terminal - I'm not sure about the system monitor as default - tends to always be system monitor at the top ;)
 
Open a terminal - apps - accessories to look at top 
 
```
top
shift +f
k
enter
```will ensure it is sorting by CPU
 
Here you go - someone who knows what they're on about :-D

---

### Post by Hippytaff on 2010-10-19
top three - Xorg, rhythmbox and pulse audio

---

### Post by GabrielYYZ on 2010-10-19
system > administration > log file viewer and check syslog. look for anything related to pulseaudio.

i had a problem earlier with pulseaudio and it was using all of my resources.

---

### Post by 4chan on 2010-10-19
@hippytaff

haha yessshhh thank you.

@gabriel

Oct 19 18:38:54 ubuntu pulseaudio[1265]: ratelimit.c: 7 events suppressedOct
19 18:38:58 ubuntu pulseaudio[1449]: pid.c: Daemon already running.
Oct 19 18:39:04 ubuntu pulseaudio[1437]: ratelimit.c: 2 events suppressed
Oct 19 18:40:57 ubuntu pulseaudio[1084]: ratelimit.c: 5 events suppressed
Oct 19 18:41:29 ubuntu pulseaudio[1299]: pid.c: Daemon already running.
Oct 19 19:01:53 ubuntu pulseaudio[1156]: ratelimit.c: 5 events suppressed
Oct 19 19:01:58 ubuntu pulseaudio[1371]: pid.c: Daemon already running.
Oct 19 19:02:02 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:02:07 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:37:02 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:38:19 ubuntu pulseaudio[1338]: ratelimit.c: 7 events suppressed
Oct 19 19:41:55 ubuntu pulseaudio[1338]: ratelimit.c: 104 events suppressed
Oct 19 19:59:36 ubuntu pulseaudio[1338]: ratelimit.c: 470 events suppressed
Oct 19 20:43:53 ubuntu pulseaudio[1384]: pid.c: Daemon already running.
Oct 19 20:45:42 ubuntu pulseaudio[1364]: ratelimit.c: 4 events suppressed

---

### Post by garethfoxwilliams on 2010-10-19
I've had this problem on two machines in the last month. Both running 10.04 Lucid.

On one, I reinstalled pulseaudio via Synaptic, which cured the problem.

On the second machine, I uninstalled pulseaudio via Synaptic and am using Jack as my server / audio router instead.

Gstreamer seems happy route into Jack, so Rhytmbox etc all play fine.

---

### Post by 4chan on 2010-10-19
> **garethfoxwilliams said:**
> I've had this problem on two machines in the last month. Both running 10.04 Lucid.

On one, I reinstalled pulseaudio via Synaptic, which cured the problem.

On the second machine, I uninstalled pulseaudio via Synaptic and am using Jack as my server / audio router instead.

Gstreamer seems happy route into Jack, so Rhytmbox etc all play fine.

Haiii Gareth thanks for your response. but i don't have problem with PulseAudio in Lucid.
and what is Jack? is it safe to just remove PulseAudio? i still can play audio and video files? 
sorry if i seems a lil paranoid but i just don't want to reinstall if something goes wrong.

also can i get notification via email if someone replying my thread?

---

### Post by Hippytaff on 2010-10-19
> 
also can i get notification via email if someone replying my thread?

 
you can subcribe to the thread in thread tools at the top of the page...there is an option to get a notification email which is defaulted to no :-)
 
excuse my stating the obvious in my previous post :-)

---

### Post by Hippytaff on 2010-10-19
> 
**Alternatives**

[ALSA]("http://www.tutorgig.com/ed/Advanced_Linux_Sound_Architecture") provides a software mixer called [dmix]("http://www.tutorgig.com/ed/Dmix"), which was developed prior to PulseAudio. This is available on almost all Linux distributions and is a simpler PCM audio mixing solution. It does not provide the advanced features (such as high quality resampling, device aggregation, timer-based scheduling and network audio) of PulseAudio.
[JACK]("http://www.tutorgig.com/ed/JACK_Audio_Connection_Kit") is in contrast to PulseAudio a professional sound server, providing real-time, [low latency]("http://www.tutorgig.com/ed/Low_latency") (e.g. 5 miliseconds and less) audio performance and since JACK2 supporting efficient load balancing by utilizing [symmetric multiprocessing]("http://www.tutorgig.com/ed/Symmetric_multiprocessing"), that is the load of all audio clients can be distributed among several processors. Audio clients can arbitrarily be connected with each other. The graph, that is all connections among JACK clients, can be visualized and edited at runtime with various applications like e.g. [Qjackctl]("http://www.tutorgig.com/ed/Qjackctl"). This makes it very intuitive to overview the overall audio control flow and to modify the routing of all audio applications and hardware at any time. JACK is the preferred sound server for professional audio applications like e.g. [Ardour]("http://www.tutorgig.com/ed/Ardour_(software)"), [Rezound]("http://www.tutorgig.com/ed/Rezound") and [LinuxSampler]("http://www.tutorgig.com/ed/LinuxSampler").
The modern implementations of the [Open Sound System]("http://www.tutorgig.com/ed/Open_Sound_System") v4 such as that by [4Front]("http://www.tutorgig.com/ed/4Front_Technologies") also provide software mixing, resampling and changing the volume on a per-application basis and, in contrast to PulseAudio, these features are implemented within the kernel. PulseAudio can also inter-operate with existing legacy sound systems, including those that were designed to exclusively lock the sound card (OSS v3).

 
from here - [http://www.tutorgig.com/ed/PulseAudio](http://www.tutorgig.com/ed/PulseAudio)

---

### Post by 4chan on 2010-10-19
@hippytaff: ahh sweet thanks for the info, ill follow gareth suggestions then, hope everything will be ok so i dont need to reinstall :3

---

### Post by GabrielYYZ on 2010-10-19
> **4chan said:**
> @hippytaff

haha yessshhh thank you.

@gabriel

Oct 19 18:38:54 ubuntu pulseaudio[1265]: ratelimit.c: 7 events suppressedOct
19 18:38:58 ubuntu pulseaudio[1449]: pid.c: Daemon already running.
Oct 19 18:39:04 ubuntu pulseaudio[1437]: ratelimit.c: 2 events suppressed
Oct 19 18:40:57 ubuntu pulseaudio[1084]: ratelimit.c: 5 events suppressed
Oct 19 18:41:29 ubuntu pulseaudio[1299]: pid.c: Daemon already running.
Oct 19 19:01:53 ubuntu pulseaudio[1156]: ratelimit.c: 5 events suppressed
Oct 19 19:01:58 ubuntu pulseaudio[1371]: pid.c: Daemon already running.
Oct 19 19:02:02 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:02:07 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:37:02 ubuntu pulseaudio[1351]: ratelimit.c: 1 events suppressed
Oct 19 19:38:19 ubuntu pulseaudio[1338]: ratelimit.c: 7 events suppressed
Oct 19 19:41:55 ubuntu pulseaudio[1338]: ratelimit.c: 104 events suppressed
Oct 19 19:59:36 ubuntu pulseaudio[1338]: ratelimit.c: 470 events suppressed
Oct 19 20:43:53 ubuntu pulseaudio[1384]: pid.c: Daemon already running.
Oct 19 20:45:42 ubuntu pulseaudio[1364]: ratelimit.c: 4 events suppressed

did you install something relating to audio recently? that might've caused the problem. that log is saying "i'm supressing events 'cause there are too many and i might be going crazy if they keep up" :P

check /etc/pulse/default.pa and see if it looks like this:

```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

edit: you posted while i was typing, if you reinstall and the problem persists, let us know. i'll leave the post unchanged anyways, just in case.

---

### Post by 4chan on 2010-10-19
nope i didn't install anything, only ubuntu restricted extras to let me play audio and video files, java, flash etc :P

my /etc/pulse/default.pa exactly looks like yours.

[http://paste.ubuntu.com/516308/](http://paste.ubuntu.com/516308/)

---

