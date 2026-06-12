---
title: "How you rip audio off of an FLV?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by cptrohn on 2009-02-03
I have some great live performances that I have saved to Video from youtube that I would like to burn to an audio CD...

Right now I have Mplayer as the only video player installed, is there a way to do this in Mplayer?  Or would VLC be the way to go?  Or do I need another package that does this?

---

### Post by cptrohn on 2009-02-03
Oh and to be more specific, I just want the Audio tracks for this, I am not wanting to convert the flash to a DVD, just rip the audio.

---

### Post by jerome1232 on 2009-02-03
This is rather simple with ffmpeg, in it's simplest form, this will re-encode the audio to mp3 and discard the video.

```
ffmpeg -i file.flv file.mp3
```

---

### Post by cptrohn on 2009-02-03
> **jerome1232 said:**
> This is rather simple with ffmpeg, in it's simplest form, this will re-encode the audio to mp3 and discard the video.

```
ffmpeg -i file.flv file.mp3
```

Thank you very much Jerome.  Do I also have to specify in terminal the exact file that I want to rip?

---

### Post by jerome1232 on 2009-02-03
Yes like say I wanted to convert the file cool-song.flv and it's in ~/Videos, and you wanted the new mp3 file to end up in ~/Music.

~/ stands for the current users home directory btw, (so for me ~/ is the same as /home/jeremy/)

```
ffmpeg -i Videos/cool-song.flv Music/cool-song.mp3
```

---

### Post by cptrohn on 2009-02-03
> **jerome1232 said:**
> Yes like say I wanted to convert the file cool-song.flv and it's in ~/Videos, and you wanted the new mp3 file to end up in ~/Music.

~/ stands for the current users home directory btw, (so for me ~/ is the same as /home/jeremy/)

```
ffmpeg -i Videos/cool-song.flv Music/cool-song.mp3
```

Oh ok, great... that sounds easy enough.

Thanks again for the help.

---

### Post by FakeOutdoorsman on 2009-02-04
You could also use FFmpeg to copy the audio stream without re-encoding.  This will preserve the quality:
[Re: How do I remove sound from a video file?](http://ubuntuforums.org/showpost.php?p=6670067&postcount=8)

---

