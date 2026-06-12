---
title: "Pulse Audio Error - It looks bad..."
date: 2009-10-23
forum: New to Ubuntu
---

### Post by samh785 on 2009-10-23
I decided to look at my log files today because I never had before, and I saw this:
```

Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop kernel: [82542.804860] 5:3:1: cannot get freq at ep 0x84
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:41:51 sam-desktop pulseaudio[14089]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Oct 22 22:42:22 sam-desktop pulseaudio[14089]: ratelimit.c: 100 events suppressed
Oct 22 23:01:28 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:02:00 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:02:18 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:02:29 sam-desktop pulseaudio[14089]: ratelimit.c: 109 events suppressed
Oct 22 23:02:46 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:03:00 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:03:14 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed
Oct 22 23:03:23 sam-desktop pulseaudio[14089]: ratelimit.c: 108 events suppressed
Oct 22 23:03:39 sam-desktop pulseaudio[14089]: ratelimit.c: 85 events suppressed
Oct 22 23:04:02 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:04:24 sam-desktop pulseaudio[14089]: ratelimit.c: 108 events suppressed
Oct 22 23:05:03 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:05:18 sam-desktop pulseaudio[14089]: ratelimit.c: 110 events suppressed
Oct 22 23:05:44 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:06:02 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:06:14 sam-desktop pulseaudio[14089]: ratelimit.c: 113 events suppressed
Oct 22 23:07:17 sam-desktop pulseaudio[14089]: ratelimit.c: 108 events suppressed
Oct 22 23:07:47 sam-desktop pulseaudio[14089]: ratelimit.c: 109 events suppressed
Oct 22 23:07:53 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:08:24 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:08:40 sam-desktop pulseaudio[14089]: ratelimit.c: 80 events suppressed
Oct 22 23:08:45 sam-desktop pulseaudio[14089]: ratelimit.c: 86 events suppressed
Oct 22 23:09:31 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:10:00 sam-desktop pulseaudio[14089]: ratelimit.c: 113 events suppressed
Oct 22 23:10:18 sam-desktop pulseaudio[14089]: ratelimit.c: 85 events suppressed
Oct 22 23:10:30 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:10:56 sam-desktop pulseaudio[14089]: ratelimit.c: 87 events suppressed
Oct 22 23:11:07 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:11:26 sam-desktop pulseaudio[14089]: ratelimit.c: 80 events suppressed
Oct 22 23:11:35 sam-desktop pulseaudio[14089]: ratelimit.c: 110 events suppressed
Oct 22 23:11:56 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:12:10 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:12:24 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:12:34 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed
Oct 22 23:13:07 sam-desktop pulseaudio[14089]: ratelimit.c: 108 events suppressed
Oct 22 23:13:23 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:13:40 sam-desktop pulseaudio[14089]: ratelimit.c: 109 events suppressed
Oct 22 23:13:55 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:14:14 sam-desktop pulseaudio[14089]: ratelimit.c: 108 events suppressed
Oct 22 23:15:03 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:15:16 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed
Oct 22 23:15:24 sam-desktop pulseaudio[14089]: ratelimit.c: 101 events suppressed
Oct 22 23:15:59 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:16:45 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:17:26 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed
Oct 22 23:17:39 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:17:47 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:18:03 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:18:10 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:18:19 sam-desktop pulseaudio[14089]: ratelimit.c: 112 events suppressed
Oct 22 23:18:34 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:18:42 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed
Oct 22 23:18:50 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:19:29 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:19:43 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:19:51 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:20:01 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:20:27 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:20:45 sam-desktop pulseaudio[14089]: ratelimit.c: 109 events suppressed
Oct 22 23:21:32 sam-desktop pulseaudio[14089]: ratelimit.c: 80 events suppressed
Oct 22 23:21:41 sam-desktop pulseaudio[14089]: ratelimit.c: 107 events suppressed
Oct 22 23:21:50 sam-desktop pulseaudio[14089]: ratelimit.c: 80 events suppressed
Oct 22 23:22:06 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:22:23 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:22:48 sam-desktop pulseaudio[14089]: ratelimit.c: 110 events suppressed
Oct 22 23:22:59 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:23:17 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:23:50 sam-desktop pulseaudio[14089]: ratelimit.c: 81 events suppressed
Oct 22 23:23:56 sam-desktop pulseaudio[14089]: ratelimit.c: 82 events suppressed
Oct 22 23:24:19 sam-desktop pulseaudio[14089]: ratelimit.c: 109 events suppressed
Oct 22 23:24:31 sam-desktop pulseaudio[14089]: ratelimit.c: 83 events suppressed
Oct 22 23:24:41 sam-desktop pulseaudio[14089]: ratelimit.c: 107 events suppressed
Oct 22 23:24:48 sam-desktop pulseaudio[14089]: ratelimit.c: 111 events suppressed
Oct 22 23:25:02 sam-desktop pulseaudio[14089]: ratelimit.c: 84 events suppressed

```This is just a small sample of the full code, and it seems to repeat itself over and over.
I can hear sound just fine, but I have noticed pulseaudio crashing on occasion.

This scares me, and I want to know what I can do to fix it...
Help!?! :confused:

---

### Post by RJARRRPCGP on 2009-10-23
OK, I'm gonna install Flash and test the audio with YouTube, BRB. ;)

---

### Post by RJARRRPCGP on 2009-10-23
I don't see anything that even looks similar in any of my logs.

---

### Post by samh785 on 2009-10-23
Maybe it has something to do with alsamixer? I'm at a loss. :P

---

### Post by RJARRRPCGP on 2009-10-23
> **samh785 said:**
> Maybe it has something to do with alsamixer? I'm at a loss. :P

Which log file?

---

### Post by samh785 on 2009-10-23
> **RJARRRPCGP said:**
> Which log file?

I just go 

System -> Administration -> Log File Viewer

and it's the default log that comes up I guess.

---

### Post by Mariane on 2009-10-23
I've had something like this when I run vlc. Mine come from the fact that the default sound output in modprobe.d is a set of usb headphones and that nowadays I mostly use loudspeakers connected to the jack. But it doesn't prevent the sound from coming out fine with vlc, so I ignore it. 

I'm not saying you should ignore it, you are probably right to look into it. 

Mariane

---

### Post by RJARRRPCGP on 2009-10-23
> **samh785 said:**
> I just go 

System -> Administration -> Log File Viewer

and it's the default log that comes up I guess.

That's what I did and nothing was found.

But, that's with Karmic Koala RC. (Testing that, right now)

Wonder if that bug was fixed for 9.10?

---

### Post by MasterProg on 2009-10-23
I found one such line:
```
Oct 23 21:40:09 masterprog-desktop pulseaudio[2676]: ratelimit.c: 189 events suppressed
```
That was three hours ago, I wonder what I was doing :D

---

### Post by samh785 on 2009-10-23
> **RJARRRPCGP said:**
> That's what I did and nothing was found.

But, that's with Karmic Koala RC. (Testing that, right now)

Wonder if that bug was fixed for 9.10?

I'm using the Karmic RC as well, so that can't be it.

Oh well I guess. At least it doesn't seem to affect me. Luckily I just bought a new laptop from system 76 so I can ditch this computer and use one that's BUILT for ubuntu. :D

---

### Post by the-spear on 2009-10-24
I am getting the same error.

I have an HDA Intel card. Running Skype, Rhythmbox, Flash vidz &/or mplayer...

---

### Post by the-spear on 2009-10-24
Jesus Samh785, your machine is a beast!

---

### Post by the-spear on 2009-10-24
TO SAMH785:
btw this is totally unrelated. your box setup is crazy. that thing is beast.

---

### Post by samh785 on 2009-10-24
haha, thanks :D

---

### Post by Lido on 2009-11-05
I'm getting no sound and plenty of these:
```
sink-input.c: Failed to create sink input: sink is suspended.
```

and a few of these:
```
pulseaudio[2412]: ratelimit.c: 9 events suppressed
```

in /var/log/messages.

any ideas?

---

### Post by basotl on 2009-11-12
I have the same error message. In my case I get that message when ever Pidgin gives me an audio notification (new message, ect.).

So far all sounds play but I get that message for certain audio events. I'm using an onboard Realtek audio chip.

---

### Post by Belizeian on 2010-02-02
Same here
following from /var/log/messages

pulseaudio[4882]: ratelimit.c: 93 events suppressed
pulseaudio[4882]: ratelimit.c: 148 events suppressed
pulseaudio[4882]: ratelimit.c: 151 events suppressed
pulseaudio[4882]: ratelimit.c: 4 events suppressed
pulseaudio[4882]: ratelimit.c: 117 events suppressed


Sound works fine just tons of entries like this in the log file, anyone figure out or know what gives?

---

### Post by Belizeian on 2010-02-19
Does anyone even care that all these log entries are being made?  It just clutters up the log files to no end for no use that I can see.  Sound works it's just these confounded log entries.

---

### Post by Belizeian on 2010-03-01
Well another week and still no answer

---

### Post by Belizeian on 2010-03-08
Another couple of weeks and still no answer

---

### Post by Belizeian on 2010-03-23
Well there goes another 2 weeks still the same issue.

---

### Post by ankspo71 on 2010-03-23
Hi,
I only have one error message like that.
```
Mar 20 17:15:56 James pulseaudio[1183]: ratelimit.c: 3 events suppressed
```This might help everyone find out what it means:
Launchpad/Google search results for: _[**site:bugs.launchpad.net pulseaudio ratelimit.c**]("http://www.google.com/search?hl=en&client=firefox&hs=XnK&rls=com.ubuntu%3Aen-US%3Aunofficial&q=site%3Abugs.launchpad.net+pulseaudio+ratelimit.c&btnG=Search&cts=1269333262243&aq=f&aqi=&aql=&oq=&gs_rfai=")_
Hope this helps.

---

### Post by cometdog on 2010-06-17
These are flooding my logs as well.  On one of the bug reports I read, the developer stated that it wasn't important and that they wouldn't fix it for 10.04 LTS.

---

### Post by Demosthenesaus on 2010-06-25
I'm getting the same.  Just did a fresh install of Ubuntu 10.4 with Audigy sound card and log is full of this error

pulseaudio[1793]: ratelimit.c: 171 events suppressed

Sound was initially not working which Gnome-alsa-mixer fixed by enabling Audigy analog output, however the error has not stopped, so appears to be unrelated.

Any thoughts anyone?

---

### Post by eluminx on 2010-07-07
i just started receiving this error after installing a new video card after my last one blew up.  But the problem is really annoying because when i try to listen to music it'll make the audio stream skip ever so often.  I would say about every minute or minute and a half.  Anyone know what the problem could be, my logs are filled with these errors, which i can live with, but the skipping of the music is extremely annoying.  Any help??

---

### Post by kyleabaker on 2010-07-09
Still no idea on the cause of this log entry?

---

### Post by etdsbastar on 2010-10-16
same problem here:

pulseaudio[1578]: ratelimit.c: 576 events suppressed

some pulseaudio error stuff. I am using Lucid. I don't know when this is going to be fixed or a better solution for this bug or error.

But, this error is giving my speakers a continuous light buzzing sound; which is stopped when I play some music. After stopping music, its again started after 2-3 minutes.

Please help.

---

