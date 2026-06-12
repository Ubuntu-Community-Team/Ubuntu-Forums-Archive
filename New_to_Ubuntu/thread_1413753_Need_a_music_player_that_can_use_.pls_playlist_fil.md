---
title: "Need a music player that can use .pls playlist files"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-22
I want to listen to [http://www.di.fm/](http://www.di.fm/)  but none of the players I have found seem compatible... can anyone recommend their favorite?

---

### Post by spcwingo on 2010-02-22
I think VLC can handle 'em.

---

### Post by NightwishFan on 2010-02-22
I bet any Gstreamer player such as Totem or Rhythmbox can use them. Totem can export to .pls files.

You may need Gstreamer plugins for AAC or Mp3. Try installing Ubuntu-Restricted-Extras package.

---

### Post by TurnOfTide on 2010-02-22
Update: none of my streaming audio works... the wierd part is that it was working... and now... zip. I can play mp3's though.

---

### Post by ridetheteapot on 2010-02-22
How does it fail?

i use mplayer for streams --- "mplayer -playlist file" (because it doesnt detect playlist files automatically)

---

### Post by TurnOfTide on 2010-02-22
There is no error, it just connects, fails... I don't see any kind of 404 or anything. I have tried various reliable stations.

---

### Post by TurnOfTide on 2010-02-22
I found this in user log....

Feb 22 07:54:46 windsor-desktop pulseaudio[3020]: module-alsa-card.c: Failed to find a working profile.
Feb 22 07:54:46 windsor-desktop pulseaudio[3020]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 08:00:32 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 08:04:29 windsor-desktop pulseaudio[1593]: module-alsa-card.c: Failed to find a working profile.
Feb 22 08:04:29 windsor-desktop pulseaudio[1593]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 08:09:11 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 08:12:56 windsor-desktop pulseaudio[1513]: module-alsa-card.c: Failed to find a working profile.
Feb 22 08:12:56 windsor-desktop pulseaudio[1513]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:05:02 windsor-desktop pulseaudio[1559]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:05:02 windsor-desktop pulseaudio[1559]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:05:51 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 18:28:35 windsor-desktop pulseaudio[1559]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:28:35 windsor-desktop pulseaudio[1559]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:29:55 windsor-desktop pulseaudio[1492]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:29:55 windsor-desktop pulseaudio[1492]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:38:36 windsor-desktop pulseaudio[1492]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:38:36 windsor-desktop pulseaudio[1492]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: pid.c: Stale PID file, overwriting.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:44:05 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 19:20:08 windsor-desktop pulseaudio[3456]: ratelimit.c: 136 events suppressed
Feb 22 20:23:35 windsor-desktop pulseaudio[3456]: ratelimit.c: 127 events suppressed
Feb 22 20:27:36 windsor-desktop pulseaudio[3456]: ratelimit.c: 37 events suppressed
Feb 22 20:27:53 windsor-desktop pulseaudio[3456]: ratelimit.c: 38 events suppressed
Feb 22 20:28:12 windsor-desktop pulseaudio[3456]: ratelimit.c: 43 events suppressed
Feb 22 20:28:26 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:28:40 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:28:50 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:29:00 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:29:14 windsor-desktop pulseaudio[3456]: ratelimit.c: 38 events suppressed
Feb 22 20:29:32 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:29:38 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:29:46 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:33:20 windsor-desktop pulseaudio[3456]: ratelimit.c: 41 events suppressed
Feb 22 20:33:55 windsor-desktop pulseaudio[3456]: ratelimit.c: 102 events suppressed
Feb 22 20:43:34 windsor-desktop pulseaudio[3456]: ratelimit.c: 104 events suppressed
Feb 22 21:07:04 windsor-desktop pulseaudio[3456]: ratelimit.c: 95 events suppressed
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Feb 22 21:32:26 windsor-desktop pulseaudio[1479]: module-alsa-card.c: Failed to find a working profile.
Feb 22 21:32:26 windsor-desktop pulseaudio[1479]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

---

### Post by NightwishFan on 2010-02-22
Please give me more information:

Is the stream mp3?
What program are you using?

Try adding the stream as an internet radio station in Rhythmbox, I play many streams like that all day.

---

### Post by TurnOfTide on 2010-02-22
It connects briefly enough to return the now playing string, but it plays no music and quickly disconnects. It is wierd because I have tried 3 different programs: none of them can stream.

---

### Post by TurnOfTide on 2010-02-22
> **NightwishFan said:**
> Please give me more information:

Is the stream mp3?
What program are you using?

Try adding the stream as an internet radio station in Rhythmbox, I play many streams like that all day.

They are all mp3, the sites are indeed up. Rythmbox fails as well. It WAS working, until I tried to install xmms2... I thought I removed it though. Youtube/flash works fine in firefox.

---

### Post by andrew.46 on 2010-02-23
Hi,

Works fine with MPlayer:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -playlist http://www.di.fm/mp3/progressive.pls[/COLOR]**
Resolving www.di.fm for AF_INET6...
Couldn't resolve name for AF_INET6: www.di.fm
Resolving www.di.fm for AF_INET...
Connecting to server www.di.fm[72.26.204.10]: 80...
Cache size set to 320 KBytes
Unknown entry type Version=2
MPlayer SVN-r30660-4.3.3 (C) 2000-2010 MPlayer Team

Playing http://scfire-mtc-aa03.stream.aol.com:80/stream/1026.
Resolving scfire-mtc-aa03.stream.aol.com for AF_INET6...
Couldn't resolve name for AF_INET6: scfire-mtc-aa03.stream.aol.com
Resolving scfire-mtc-aa03.stream.aol.com for AF_INET...
Connecting to server scfire-mtc-aa03.stream.aol.com[64.12.61.3]: 80...
Name   : Progressive - D I G I T A L L Y - I M P O R T E D - house, techno, and trance beats for your mind!
Genre  : Electronic Progressive House Trance
Website: http://www.di.fm
Public : yes
Bitrate: 96kbit/s
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='Manolis Beis - Red Ocean III (December 2009)';StreamUrl='';
Cache fill: 17.50% (57344 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.5 (07.5) of -0.0 (unknown)  0.7% 68% 

```

Can you duplicate my efforts and post the terminal output?

All the best,

Andrew

---

### Post by ikt on 2010-02-23
> **TurnOfTide said:**
> I found this in user log....

```
Feb 22 07:54:46 windsor-desktop pulseaudio[3020]: module-alsa-card.c: Failed to find a working profile.
Feb 22 07:54:46 windsor-desktop pulseaudio[3020]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 08:00:32 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 08:04:29 windsor-desktop pulseaudio[1593]: module-alsa-card.c: Failed to find a working profile.
Feb 22 08:04:29 windsor-desktop pulseaudio[1593]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 08:09:11 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 08:12:56 windsor-desktop pulseaudio[1513]: module-alsa-card.c: Failed to find a working profile.
Feb 22 08:12:56 windsor-desktop pulseaudio[1513]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:05:02 windsor-desktop pulseaudio[1559]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:05:02 windsor-desktop pulseaudio[1559]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:05:51 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 18:28:35 windsor-desktop pulseaudio[1559]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:28:35 windsor-desktop pulseaudio[1559]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:29:55 windsor-desktop pulseaudio[1492]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:29:55 windsor-desktop pulseaudio[1492]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:38:36 windsor-desktop pulseaudio[1492]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:38:36 windsor-desktop pulseaudio[1492]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: pid.c: Stale PID file, overwriting.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: module-alsa-card.c: Failed to find a working profile.
Feb 22 18:42:50 windsor-desktop pulseaudio[3456]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 22 18:44:05 windsor-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 22 19:20:08 windsor-desktop pulseaudio[3456]: ratelimit.c: 136 events suppressed
Feb 22 20:23:35 windsor-desktop pulseaudio[3456]: ratelimit.c: 127 events suppressed
Feb 22 20:27:36 windsor-desktop pulseaudio[3456]: ratelimit.c: 37 events suppressed
Feb 22 20:27:53 windsor-desktop pulseaudio[3456]: ratelimit.c: 38 events suppressed
Feb 22 20:28:12 windsor-desktop pulseaudio[3456]: ratelimit.c: 43 events suppressed
Feb 22 20:28:26 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:28:40 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:28:50 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:29:00 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:29:14 windsor-desktop pulseaudio[3456]: ratelimit.c: 38 events suppressed
Feb 22 20:29:32 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:29:38 windsor-desktop pulseaudio[3456]: ratelimit.c: 39 events suppressed
Feb 22 20:29:46 windsor-desktop pulseaudio[3456]: ratelimit.c: 40 events suppressed
Feb 22 20:33:20 windsor-desktop pulseaudio[3456]: ratelimit.c: 41 events suppressed
Feb 22 20:33:55 windsor-desktop pulseaudio[3456]: ratelimit.c: 102 events suppressed
Feb 22 20:43:34 windsor-desktop pulseaudio[3456]: ratelimit.c: 104 events suppressed
Feb 22 21:07:04 windsor-desktop pulseaudio[3456]: ratelimit.c: 95 events suppressed
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 22 21:14:04 windsor-desktop pulseaudio[3456]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Feb 22 21:32:26 windsor-desktop pulseaudio[1479]: module-alsa-card.c: Failed to find a working profile.
Feb 22 21:32:26 windsor-desktop pulseaudio[1479]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```

What sound card do you have?

Every media player has no problem with di.fm streams, I'm listening to it right now..

---

### Post by chillicampari on 2010-02-23
Have you tried rebooting to see if it clears up?

---

### Post by Jeff Anthony on 2010-02-23
As an answer to both the query for a favorite .pls player and a possible solution to the audio problem I'd suggest Mozilla's Songbird. It's really that good! Just download the debian package and install! Direct the player to your music folder when first opening and Songbird organizes it complete with album art and song lyrics. 

I do see a trend for Mozilla and would love to see apps to manage our video, documents and images available across both physical and Ubuntu One or Picasa style cloud storage.

---

### Post by TurnOfTide on 2010-02-23
Update: Mplayer works, my soundcard is onboard (Mobo: Asus-MPN-PV micro atx).

Odd how no other player works....

---

### Post by andrew.46 on 2010-02-24
Hi Turn,

> **TurnOfTide said:**
> Odd how no other player works....

Hmmm.... I am on another distro but vlc plays the same address well enough... screenshot attached.

Andrew

---

