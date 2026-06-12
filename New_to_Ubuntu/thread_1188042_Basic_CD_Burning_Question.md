---
title: "Basic CD Burning Question"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by CompBio on 2009-06-15
I want to burn some CDs for a road trip from music I've already got stored (.mp3 and .m4a) on my laptop.  My files are fairly small: on average, one albums' worth of music is ~25-40 MB.  So I figured with a 700 MB writeable CD, I should be able to store several albums' worth of music.  However, Brasero only allots about 90 minutes' worth for a new CD project.

I've also used streamripper to capture some Prairie Home Companion broadcasts precisely for replaying on road trips.  Each episode is 2 hrs., which already exceeds this 90-minute limitation.  However, again, each file is about 60 MB, so I figured I should be able to store at least 10 of these on a single CD.

Is this a Brasero limitation?  A limitation for standard CD players?

Thanks!

---

### Post by marshall.robert on 2009-06-15
Perhaps you are trying to make an *Audio CD*, rather than a *Data CD*.

The difference is that an Audio CD has the time limitation whereas the Data CD has the space limitation. Audio CDs are like the albums you buy from shops and should work in all CD players. Data CDs can hold anything but if you have just MP3s, for example, you can fit a lot more music that way but you do need a cd player capable of reading MP3 files.

I fear what I just said it useless but it is the only thing I can think of that relates to your problem.

---

### Post by Cheesemill on 2009-06-15
You're trying to burn an Audio CD. This will convert your mp3s into a format readable by normal Hi-Fi CD players (hence the 90min maximum).

If you just want to burn the mp3 files to a CD so that you can play them back on a PC then you need to choose 'Data Project' instead of 'Audio Project' when starting Brassero.
Just note that a Data CD won't be playable in a normal CD player (although some players are mp3 compatible, they'll usually have the mp3 logo on them).

---

### Post by Therion on 2009-06-15
Your .mp3's are being converted to an audio CD format by your burning software by default.  If you want to play the actual .mp3 files you will need a CD player that allows for that (lots of older set-top and in-car CD players don't play .mp3).

The conversion of your .mp3 files to the audio-CD format is why you only get an hour and half or so of music on a CD.

Most likely you just need to adjust some settings on your burning software however in order to burn an .mp3 CD.  Just be sure you player(s) support it.

---

### Post by CompBio on 2009-06-15
Wow, thanks for such rapid responses!

Sorry, I should have been clearer -- yes, I'm trying to burn audio CDs that we can play on our car CD player.  It sounds as if the limitation is in the CD players themselves (a bit galling to waste so much disk space), but at least now I know the problem.


Next question (and I know I should RTFM, but as long as we're on the subject), is there a way to load a playlist into Brasero instead of using the browser window to select tracks?

---

### Post by zerhacke on 2009-06-15
> **CompBio said:**
> 
Next question (and I know I should RTFM, but as long as we're on the subject), is there a way to load a playlist into Brasero instead of using the browser window to select tracks?
Sort of.  You could create a cue file to send to Brasero, but this would take longer than just manually adding the files.

---

### Post by rogueleader12345 on 2009-06-15
Also, if Brasero is giving you problems, install Serpentine. It is strictly an audio cd creator. Very easy to use. Just be careful, if it says that it can't find the cache, that means you have less than 700MB of disk space left on whatever you are booting Ubuntu off of ;)

---

### Post by CompBio on 2009-06-15
> **rogueleader12345 said:**
> Also, if Brasero is giving you problems, install Serpentine. It is strictly an audio cd creator. Very easy to use. Just be careful, if it says that it can't find the cache, that means you have less than 700MB of disk space left on whatever you are booting Ubuntu off of ;)

Well spotted.  Brasero thought my new, blank CD had no space on it.  So I tried Serpentine and it worked just fine.  \\:D/

---

### Post by rogueleader12345 on 2009-06-15
Glad I could be of some assistance!

---

### Post by gsocker on 2009-06-15
Actually, audio CDs store about 840MB of audio data, compared to data CDs 700MB max. There's far less error correction on them as small errors are much less of a problem for audio that computer data. What's probably getting you is this:
 At the typical default rate for MP3 files(128 kbit/s) you use ~ 1MB per minute. The streamed source is probably even less - around 32-64 kbit/s is typical.
It probably is also at a lower sampling rate - maybe 22KHz or lower, or is mono only.
"Red Book" CD audio, however, at 44.1KHz and 2 byte samples,
occupies 10MB per minute, 10x the disk space of MP3 or AAC at 128kbit/s. 
This is where the problem comes in:
A 2 hour program at the default rates "expands" from ~120MB to nearly 1200MB when uncompressed. Unfortunately, there is no way around this, since Audio CDs support only the one rate.

---

