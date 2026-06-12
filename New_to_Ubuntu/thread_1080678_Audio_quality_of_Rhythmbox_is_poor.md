---
title: "Audio quality of Rhythmbox is poor"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-02-25
Hi there, 

I have been having problems playing mp3 files in rhythmbox. Basically I have a mix of CD ripped and internet downloaded (amazon) songs all at various bitrates.

When I play a song on Rhythmbox it sounds worse than when I play it off my iPod. 

The speakers are the same, the volume settings are (pretty much) the same. The song is the same.

Why does this happen? Can it be fixed?

Thanks,

---

### Post by Testrum on 2009-02-25
I recommend downloading Songbird from [http://www.getdeb.net/](http://www.getdeb.net/) since the official Songbird website doesn't have a Ubuntu repo.

---

### Post by abhiroopb on 2009-02-25
Thanks, but I'm quite comfortable with Rhythmbox for now, and don't really want to change unless there is NO way to solve the problem. Although I think I will give Songbird a try (heard good things about it!)

---

### Post by Testrum on 2009-02-25
> **abhiroopb said:**
> Thanks, but I'm quite comfortable with Rhythmbox for now, and don't really want to change unless there is NO way to solve the problem. Although I think I will give Songbird a try (heard good things about it!)
Songbird has iPod compatibility built into it, Shoutcast radio, iTunes style layout, and great sound quality.

---

### Post by abhiroopb on 2009-02-25
persuasive arguments...I've decided to try it out. But I've been a fan of rhythmbox for a while and was wondering if anyone can help with the poor sound quality, is it a known issue?

---

### Post by Bölvaður on 2009-02-25
elaborate on "poor sound quality"
and can you make sure it isn't just the audio card or the mp3 codec which is the cause.

This sounds too tricky to know where to begin, so those things should be a good place to narrow down the problem and define it better.

---

### Post by abhiroopb on 2009-02-25
I'll try to clarify:

1. Poor - I plug in the ipod to listen and compare it to rhythmbox, and rhythmbox sounds "scratchier", not as clear as the sound from the iPod. Also there is a hiss (sometimes). 

2. Audio card - could be, but I mean what could be wrong with it? I've had my laptop for a while and it seems to be running fine.

3. MP3 codec - I have the standard ubuntu restricted extras package installed.

- It may have something to do with the whole pulse-audio sound issue, but not really sure what to do about it. I used the following guide to fix pulse: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Bölvaður on 2009-02-25
if you have problem with pulse, then most people just go to alsa and dont see any difference.

I would have to be on the place to understand the problem :( I wish you good luck

---

### Post by TeeRev on 2009-02-26
I'm also not all that satisfied with the quality of rhythmbox.  I have a 10 band equalizer plugin, but it almost sounds as if it makes it worse for certain songs (same sort of thing, scratchy, background noise almost), and without the EQ it just sounds flat.  I have a dual boot with XP, and I use media monkey for music in XP, and it definitely sounds a lot better.  As for switching to other media players in ubuntu, I've tried exaile, but it was way slower than rhythmbox is for the size of my library (16000+).  I've heard good things about Amarok, and songbird, but I haven't been able to really find out if they can handle a large library well or not.  Anyone know?

---

### Post by RazielSedai on 2009-02-27
I have the same problem with Audacious.  I've installed Winamp via Wine, and the sound quality is great, so I assume it's not a problem with my sound card.  I also don't have any problem when I'm using Winamp in Windows, which I'm dual-booting.  I've also tried exporting my Winamp equalizer settings (I use the Full Bass and Treble preset) and when I import it into Audacious, the sounds is extremely tinny.  When I don't use the equalizer at all, the sound seems flat.

I've switched between PulseAudio, OSS, and ALSA, and it all sounds the same.

I'd use Winamp, but it tends to crash randomly, and I'd rather be using Audacity anyway.

Maybe this will help clear up what the problem might be, because it seems you're having the same problem as me.

---

### Post by stchman on 2009-02-27
> **TeeRev said:**
> I'm also not all that satisfied with the quality of rhythmbox.  I have a 10 band equalizer plugin, but it almost sounds as if it makes it worse for certain songs (same sort of thing, scratchy, background noise almost), and without the EQ it just sounds flat.  I have a dual boot with XP, and I use media monkey for music in XP, and it definitely sounds a lot better.  As for switching to other media players in ubuntu, I've tried exaile, but it was way slower than rhythmbox is for the size of my library (16000+).  I've heard good things about Amarok, and songbird, but I haven't been able to really find out if they can handle a large library well or not.  Anyone know?

Sound quality on my system using Rhythmbox is excellent.

Where did you get the equalizer plugin for Rhythmbox?

---

### Post by abhiroopb on 2009-03-01
I have been using Songbird for the past few days (ver 1.0) and the sound quality is amazing! MUCH better than rhythmbox. It is VERY buggy, and slow, however, the most important aspect (sound quality) is great!

Wish it was part of the repos, and supported iPod album art, but other than that its perfect!

---

### Post by orange smartie on 2009-03-06
I too have noticed a scratchiness in the sound quality of Rythmbox.I improved my sound quality in the audio control panel by lowering the PCM setting and raising the master volume. Seems to work. Don't know why!

---

### Post by TrombaMarina on 2009-09-29
You are hearing distortion from the preamp volume being set too high for your sound card.  There is a little speaker icon in the right-hand side of the Rhythmbox buttons bar that allows you to set the preamp volume.  Set it at exactly 49% and leave it there.  Control the overall volume with the system volume control instead (mapped to the keyboard volume controls by default).  The sound quality should be exactly the same as iTunes when no EQ is used (just figured this out myself).

iTunes has EQ and an option to automatically raise the volume of quiet songs which can make them hard to compare.  Rhythmbox can do that too (it's [ReplayGain]("http://en.wikipedia.org/wiki/Replay_Gain#Replay_Gain-compliant_audio_players") compliant), but you enable it from GConf (System -> Administration -> Services, click "Unlock", put a check next to "Audio Settings Management").  After that, you may want to keep your Rhythmbox volume around 12%.  If you use EQ (where is that plug-in?) with Rhythmbox, be careful not to set any frequency too loud.  You might want to only cut frequencies, not increase, to avoid overdriving the preamp.

I prefer Rhythmbox to Songbird because it uses less system resources and sounds great (once you get it adjusted).

All that said, I'm looking forward to the sound system updates in Karmic Koala.  Also, a system-wide EQ would be better than an application specific one because I use EQ to compensate for shortcomings in my headphones, soundcard, and speakers (or maybe to tune it to the room).  I never use it per-song.

---

### Post by expxe on 2009-12-04
> **TrombaMarina said:**
> You are hearing distortion from the preamp volume being set too high for your sound card.  There is a little speaker icon in the right-hand side of the Rhythmbox buttons bar that allows you to set the preamp volume.  Set it at exactly 49% and leave it there.  Control the overall volume with the system volume control instead (mapped to the keyboard volume controls by default).  The sound quality should be exactly the same as iTunes when no EQ is used (just figured this out myself).

iTunes has EQ and an option to automatically raise the volume of quiet songs which can make them hard to compare.  Rhythmbox can do that too (it's [ReplayGain]("http://en.wikipedia.org/wiki/Replay_Gain#Replay_Gain-compliant_audio_players") compliant), but you enable it from GConf (System -> Administration -> Services, click "Unlock", put a check next to "Audio Settings Management").  After that, you may want to keep your Rhythmbox volume around 12%.  If you use EQ (where is that plug-in?) with Rhythmbox, be careful not to set any frequency too loud.  You might want to only cut frequencies, not increase, to avoid overdriving the preamp.

I prefer Rhythmbox to Songbird because it uses less system resources and sounds great (once you get it adjusted).

All that said, I'm looking forward to the sound system updates in Karmic Koala.  Also, a system-wide EQ would be better than an application specific one because I use EQ to compensate for shortcomings in my headphones, soundcard, and speakers (or maybe to tune it to the room).  I never use it per-song.

good advice

---

### Post by MooPi on 2009-12-04
Maybe it's time to go old school and try a console player like "cplay".  I use it exclusively without issue but I rip all my songs and music directly from CD. and I know the quality is superb. Small footprint and easy to learn commands.

---

### Post by brookie on 2009-12-04
Any idea how to do this in Karmic? :)

[quote=
iTunes has EQ and an option to automatically raise the volume of quiet songs which can make them hard to compare.  Rhythmbox can do that too (it's [ReplayGain]("http://en.wikipedia.org/wiki/Replay_Gain#Replay_Gain-compliant_audio_players") compliant), but you enable it from GConf (System -> Administration -> Services, click "Unlock", put a check next to "Audio Settings Management").  After that, you may want to keep your Rhythmbox volume around 12%.  If you use EQ (where is that plug-in?) with Rhythmbox, be careful not to set any frequency too loud.  You might want to only cut frequencies, not increase, to avoid overdriving the preamp.[/quote]

---

### Post by abhiroopb on 2009-12-05
I use amarok which is amazing. Unfortunately, my speakers like to hiss at me constantly!..[http://ubuntuforums.org/showthread.php?t=925739](http://ubuntuforums.org/showthread.php?t=925739)

---

### Post by SR_ELPIRATA on 2009-12-07
Only times Ive had audio problems were when I moved to 9.10 with a clean install. To me Rhythmbox sounds excellent (its connected to my home theather system) and even playing 128kbs files sound very nice.

ELP

---

### Post by arthur.afarias on 2010-04-03
> **TrombaMarina said:**
> You are hearing distortion from the preamp volume being set too high for your sound card.  There is a little speaker icon in the right-hand side of the Rhythmbox buttons bar that allows you to set the preamp volume.  Set it at exactly 49% and leave it there.  Control the overall volume with the system volume control instead (mapped to the keyboard volume controls by default).  The sound quality should be exactly the same as iTunes when no EQ is used (just figured this out myself).

iTunes has EQ and an option to automatically raise the volume of quiet songs which can make them hard to compare.  Rhythmbox can do that too (it's [ReplayGain]("http://en.wikipedia.org/wiki/Replay_Gain#Replay_Gain-compliant_audio_players") compliant), but you enable it from GConf (System -> Administration -> Services, click "Unlock", put a check next to "Audio Settings Management").  After that, you may want to keep your Rhythmbox volume around 12%.  If you use EQ (where is that plug-in?) with Rhythmbox, be careful not to set any frequency too loud.  You might want to only cut frequencies, not increase, to avoid overdriving the preamp.

I prefer Rhythmbox to Songbird because it uses less system resources and sounds great (once you get it adjusted).

All that said, I'm looking forward to the sound system updates in Karmic Koala.  Also, a system-wide EQ would be better than an application specific one because I use EQ to compensate for shortcomings in my headphones, soundcard, and speakers (or maybe to tune it to the room).  I never use it per-song.

Good advice! I just adjusted the rhithmbox sound volume for something close to 50% and everything worked perfectly.

---

### Post by lidex on 2010-04-03
Songbird users beware, support for linux is being dropped:
[Songbird halts major support for linux]("http://www.ubuntugeek.com/songbird-halts-major-support-for-linux.html")

---

