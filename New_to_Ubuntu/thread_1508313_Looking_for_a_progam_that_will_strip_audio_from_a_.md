---
title: "Looking for a progam that will strip audio from a video file."
date: 2010-06-12
forum: New to Ubuntu
---

### Post by DarkDancer on 2010-06-12
I, well, need the above. Probably mostly for avi's but would like multiformat of course....

---

### Post by NFblaze on 2010-06-12
PiTiVi will do this.

Normally you have to ungroup the video and audio first from within the program, then just delete the audio. Good Luck.

---

### Post by DarkDancer on 2010-06-12
Thanks, I'll ty it, needing to delete the video and keep the audio though.

---

### Post by dizmayed on 2010-06-12
I use the Audacity audio recorder/editor to record the audio from musical performance videos, for example. It's quite versatile, lets you select the audio file format, customize quality, etc.

I think that's what you're looking for.


[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

---

### Post by dtfinch on 2010-06-12
With ffmpeg, it should be something like:
ffmpeg -i videofilename -vn -acodec copy audiofilename
making sure that the audio file extension matches the audio format in the video.

---

### Post by NFblaze on 2010-06-12
Oh in that case, if you just want the AUDIO from a video file.

use "Sound Converter" in the Applications > Sound & Video menu.

I use it all the time to strip audio from a video. Though normally I go from the common proprietary encode (AAC, MP3) to OGG Vorbis. So I dont know if it will work from MP3 to MP3. Good Luck.

This method is much quicker and simpler

---

### Post by DarkDancer on 2010-06-12
I went with NFblaze's suggestion of Sound Converter, but thank you all for the input... ;)

---

