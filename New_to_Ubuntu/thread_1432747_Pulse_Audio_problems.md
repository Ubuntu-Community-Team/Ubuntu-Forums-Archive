---
title: "Pulse Audio problems"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-03-18
ar 18 20:34:41 pj-indulgence pulseaudio[10081]: ratelimit.c: 2 events suppressed
Mar 18 20:34:46 pj-indulgence pulseaudio[10081]: ratelimit.c: 2 events suppressed
Mar 18 20:34:56 pj-indulgence pulseaudio[10081]: ratelimit.c: 1 events suppressed
Mar 18 20:35:43 pj-indulgence pulseaudio[10081]: last message repeated 5 times
Mar 18 20:35:43 pj-indulgence pulseaudio[10081]: ratelimit.c: 4 events suppressed
Mar 18 20:35:54 pj-indulgence pulseaudio[10081]: ratelimit.c: 2 events suppressed
Mar 18 20:36:25 pj-indulgence pulseaudio[10081]: ratelimit.c: 2 events suppressed
Mar 18 20:36:30 pj-indulgence pulseaudio[10081]: ratelimit.c: 1 events suppressed
Mar 18 20:37:11 pj-indulgence pulseaudio[10081]: last message repeated 3 times
Mar 18 20:37:11 pj-indulgence pulseaudio[10081]: ratelimit.c: 5 events suppressed
Mar 18 20:37:22 pj-indulgence pulseaudio[10084]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Mar 18 20:38:45 pj-indulgence pulseaudio[10084]: last message repeated 3 times
Mar 18 20:58:15 pj-indulgence pulseaudio[10084]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Mar 18 20:59:16 pj-indulgence pulseaudio[10084]: last message repeated 3 times
Mar 18 20:59:54 pj-indulgence pulseaudio[10081]: ratelimit.c: 1 events suppressed
Mar 18 21:00:57 pj-indulgence pulseaudio[10081]: last message repeated 2 times
Mar 18 21:01:02 pj-indulgence pulseaudio[10081]: ratelimit.c: 8 events suppressed
Mar 18 21:01:07 pj-indulgence pulseaudio[10081]: ratelimit.c: 12 events suppressed
Mar 18 21:01:12 pj-indulgence pulseaudio[10081]: ratelimit.c: 12 events suppressed
Mar 18 21:01:17 pj-indulgence pulseaudio[10081]: ratelimit.c: 16 events suppressed
Mar 18 21:01:22 pj-indulgence pulseaudio[10081]: ratelimit.c: 9 events suppressed
Mar 18 21:01:27 pj-indulgence pulseaudio[10081]: ratelimit.c: 14 events suppressed


I get a huge number of pulseaudion errors in my log file. Should I remove PulseAudio from my system? What should I replace it with?

---

### Post by Psumi on 2010-03-18
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio

then

sudo apt-get install alsa-utils gstreamer0.10-x

Your volume applet in gnome panel will no longer function after this, as it's geared to work only with pulse.

You'll want to run gstreamer-properties and make sure that everything for audio/video output are set to Automatic.

---

### Post by dunbrokin on 2010-03-18
Thanks for that....lets see how it goes.

---

### Post by lagrang on 2010-03-27
Hi, i want to share that the sound start to work as soon as i purge pulseaudio, i have had already installed gsstream, when i start to look up for a solution.

Thank you very much for the sugestion.

---

