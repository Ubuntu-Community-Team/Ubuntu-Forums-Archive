---
title: "How to extract audio files from DVD?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by sundol on 2009-03-07
I want to extract audio data from a DVD. 
I don't care much about audio format. (.mp3 or .ogg)

Can you recommend any good software for this purpose?

---

### Post by &#22247;.weive on 2009-03-07
Try Dvdrip&#65311;I didn't use this software,just a suggestion.
By the way ,can soundjuicer work?

---

### Post by 3rdalbum on 2009-03-07
I have used DVD:Rip for this. After extracting the audio files, you generally need to put them into Audacity and edit them into chapters, and then output them at 44.1kHz. (DVD audio is usually at 48kHz, but CD audio is 44.1kHz, hence the reason for the conversion).

Bear in mind that DVD:Rip isn't the most user-friendly software around. If you get an error message about a missing folder, then you need to create the folder that it's complaining about.

---

### Post by Jose Catre-Vandis on 2009-03-07
Have mplayer/mencoder installed:

This will extract audio track no. 128, downmix the AC3 sound to PCM and write the results to file.wav:
```
mplayer -vo null -hardframedrop -aid 128 -ao pcm -aofile file.wav dvd://1
```

This will extract the audiofrom a video file, convert it to PCM and write the resulting wave file to audio.wav:

```
mplayer -vo null -hardframedrop -ao pcm:file=audio.wav myvideo.avi
```

Using ffmpeg for a video file:
```
ffmpeg -i input.avi -vn output.mp3
```

---

### Post by andrew.46 on 2009-03-07
Hi,

I know it will be a hard thing to sell but the newest Transcode will do this very *neatly*. If you wished to *rip* a single audio track from title 1, chapter 1 of a dvd and then *transcode* it to mp3 the following single command will do all of this:

```
transcode -x dvd -i /dev/dvd -T 1,1,1 -a 0 -y null,tcaud \
--lame_preset standard -E 44100,16,2 -m $HOME/Desktop/output.mp3
```

How cool is that!! The syntax will be relevant only to the newest Transcode, I am using:

```
andrew@skamandros~$ transcode --version
transcode v1.1.1 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
```

All the best,

Andrew

---

