---
title: "Computer freezes due to suppressed audio events?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by woodmaster on 2009-12-29
Ok.  I have dumped Windows and installed 9.10 Karmic on my Dell Dimension 2400.  Most everything is great, but...I get _random_ freezing.  I tried a lot of things except dumping and reverting to 8.04.  The last thing I did was to upgrade the Linux Kernel which seemed to help.  I ran Youtube playing a video, uploading a video, had pictures open in Gimp, and text files open as well as seperate web browsers doing things, all of this trying to make it freeze again, couldn't do it.  Then, this morning with nothing open, only my applications tab going to the app I wanted to open, it froze...almost.  It stopped for a little but I could still use the mouse, but it wouldn't let me open anything or compress the sub menu when I moved the mouse back over.  Then after a few seconds(15-30 maybe), it let me open a program and now everything seems fine.  I have seen a lot of people saying 9.10 has a lot of glitches, but I don't want to reinstall if I don't have to.  I am not sure what this means, but my log file at that time showed this in the messages tab:
Dec 29 11:30:54 Sam-Jenn pulseaudio[1477]: ratelimit.c: 8 events suppressed
Dec 29 11:31:00 Sam-Jenn pulseaudio[1477]: ratelimit.c: 7 events suppressed
Dec 29 11:36:44 Sam-Jenn pulseaudio[1477]: ratelimit.c: 2 events suppressed
Dec 29 11:36:50 Sam-Jenn pulseaudio[1477]: ratelimit.c: 6 events suppressed
Dec 29 11:36:55 Sam-Jenn pulseaudio[1477]: ratelimit.c: 7 events suppressed
Dec 29 11:37:00 Sam-Jenn pulseaudio[1477]: ratelimit.c: 3 events suppressed
Dec 29 11:37:05 Sam-Jenn pulseaudio[1477]: ratelimit.c: 2 events suppressed
Dec 29 11:37:11 Sam-Jenn pulseaudio[1477]: ratelimit.c: 8 events suppressed
Dec 29 11:37:16 Sam-Jenn pulseaudio[1477]: ratelimit.c: 4 events suppressed
Dec 29 11:49:44 Sam-Jenn pulseaudio[1477]: ratelimit.c: 2 events suppressed
Dec 29 12:00:38 Sam-Jenn pulseaudio[1477]: ratelimit.c: 10 events suppressed
Why so many audio events?  and whay are they being suppressed?  I really don't understand 90% of what is in the log files.  Any help will be appreciated.  I am barely holding off my wife from making me reinstall Windows. She's convinced Ubuntu hates her.  All the crashes show a similar thing in the log file BTW.  Suppressed audio events multiple times.

---

### Post by natravis on 2009-12-29
There are some known issues with PulseAudio and a package called udev (I believe). I believe the only workaround, at the moment, is to install ALSA as your audio manager while the devs get Pulse playing nicely. There are threads that can tell you how to do that. Hope this helps!

---

