---
title: "Exact Audio Copy"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by RichardCL on 2010-01-03
Dear Forum,

As my CD player died just recently, I decided to replace with a media PC running Ubuntu to play CDs and DVDs. Then I realized that I can convert all my music to some lossless format and put the CDs in the cellar. The point being that the kids (who destroyed said CD player) won't then be able to get hold of the CDs.

For Windows I used to have [EAC]("http://http://www.exactaudiocopy.de/") to read CDs and make perfect copies. The program reads multiple times to ensure a perfect copy.

Is there a similar program for Ubuntu?

EAC should work in Virtual Box or Wine but I'd rather have something native.

---

### Post by meho_r on 2010-01-03
[Grip.](http://nostatic.org/grip/)

---

### Post by Guitar John on 2010-01-03
FLAC is a compressed but completely lossless format.  Your cd collection will be about one-half of the file size of the .wav files but with no loss in quality.

---

### Post by falconindy on 2010-01-03
RubyRipper is similar to EAC in its multi-read behavior.

---

### Post by lhb1142 on 2010-01-03
> **RichardCL said:**
> Dear Forum,

As my CD player died just recently, I decided to replace with a media PC running Ubuntu to play CDs and DVDs. Then I realized that I can convert all my music to some lossless format and put the CDs in the cellar. The point being that the kids (who destroyed said CD player) won't then be able to get hold of the CDs.

For Windows I used to have [EAC]("http://http://www.exactaudiocopy.de/") to read CDs and make perfect copies. The program reads multiple times to ensure a perfect copy.

Is there a similar program for Ubuntu?

EAC should work in Virtual Box or Wine but I'd rather have something native.

I use Asunder CD Ripper or, more frequently, Audio CD Ripper [Sound Juicer]. I rip the CDs as their normal .wav files. (Both claim to obtain track information but Audio CD Ripper appears to be better in that regard.)

When the ripping is complete, I then convert these files to the FLAC format using Sound Converter. (Using Sound Converter, I can convert almost any audio format into almost any other audio format that I may want.)

This double process ensures that the ripping and conversion is done perfectly. You will hear no difference whatsoever in the sound quality.

All of these programs are available in the Synaptics Package Manager.

---

### Post by RichardCL on 2010-01-11
Many thanks for the comments. Ruby Ripper is installed and seems to be doing just what I want, including some great features like ripping to multiple formats concurrently.

---

### Post by jis on 2010-01-17
@lhb1142: If I remember right, sound-juicer can make flac files, too. But I am not able to move position of playback of such files randomly in alsaplayer-gtk in ubuntu 9.10. Is it the same with flac files made by Sound Converter?

---

### Post by lhb1142 on 2010-01-17
> **jis said:**
> @lhb1142: If I remember right, sound-juicer can make flac files, too. But I am not able to move position of playback of such files randomly in alsaplayer-gtk in ubuntu 9.10. Is it the same with flac files made by Sound Converter?
 
I'm sorry but I don't know the answer to your question about moving position of FLAC files. As I exclusively make FLAC files from classical works, I naturally play them in the order in which they're recorded. But you are correct - you can indeed make FLAC files using Audio CD Extractor (Sound Juicer).

Also, I do not use the alsaplayer-gtk; the players I use when playing music through my computer are VLC, Audacious2, and SMPlayer. The choice of player depends on how each one handles a particular folder in which I have my FLAC files; sometimes one or more of the players will "want" to play files out of order but there is always at least one of the players which will play them properly.

I also recently bought an inexpensive [Western Digital media player]("http://www.amazon.com/Western-Digital-Media-Player-WDBAAL0000NBK-NESN/dp/B002KG0JMG/ref=sr_1_4?ie=UTF8&s=electronics&qid=1263747721&sr=8-4") which allows me to play my FLAC (or any other kind of) files stored on an external hard drive through my stereo system without the use of a computer. Of course you need a computer to put the files on the hard drive in the first place, but then you can just play your music.

FLAC files sound fine, no different than CDs (I've compared a FLAC file with the CD from which it was derived).

---

### Post by jis on 2010-01-17
@lhb1142: I did not mean the order in which tracks are played, but ability to drag playback position within a track. I use alsaplayer-gtk sometimes, because it has nice controls for balance and playback speed and direction.

---

### Post by lhb1142 on 2010-01-18
> **jis said:**
> @lhb1142: I did not mean the order in which tracks are played, but ability to drag playback position within a track. I use alsaplayer-gtk sometimes, because it has nice controls for balance and playback speed and direction.

I'm sorry I misunderstood your question. I cannot comment on the alsaplayer-gtk as I do not use it but it is quite easy to "fast-forward" or "rewind" an individual track (by dragging the indicator) when using any of the players I mentioned: VLC, Audacious2, or SMPlayer. (It is helpful to have the players "maximized" in size to make the position indicator larger.)

This works with any of the file types I have tried, including FLAC.

I hope this helps you.

Lawrence

---

### Post by HDave on 2010-04-21
> **meho_r said:**
> [Grip.](http://nostatic.org/grip/)

I've been a happy user of GRIP for a long time, but sadly it is not longer in the repositories.  Apparently it is dead...

---

