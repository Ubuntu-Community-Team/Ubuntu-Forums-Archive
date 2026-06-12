---
title: "Encoding .wav files"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Thelasko on 2009-04-14
What package do I need to encode .wav files?

Thanks

---

### Post by durand on 2009-04-14
Try sound converter.
```
sudo aptitude install soundconverter
```

---

### Post by Thelasko on 2009-04-14
I tried soundconverter, it didn't work.  I think I'm missing a codec.

---

### Post by durand on 2009-04-14
What exactly are you trying to do? If you go to preferences, you can change the format that you want to encode to.

---

### Post by Thelasko on 2009-04-14
Convert an ogg into a wav file.  All I got was a large file that won't play.

---

### Post by durand on 2009-04-14
Well, you could open it in audacity or soundkonverter (different program) or try mencoder.

---

### Post by Didius Falco on 2009-04-14
Audacity is my sound converter/editor of choice. It needs "libmp3lame0"*.* I couldn't find it through the Add/Remove option, but Synaptic found it via a search right away. 

Here is a guide to how to enable MP3 export in Audicity: [http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

---

### Post by durand on 2009-04-14
Audacity works but it's not particularly useful when you have many files to convert since it is quite slow and you have to do everything manually.

---

### Post by Didius Falco on 2009-04-14
> **Thelasko said:**
> I tried soundconverter, it didn't work.  I think I'm missing a codec.

For SoundConverter MP3 encoding, here is a website with a link to the required codec:

[http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/](http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/)

---

### Post by garyed on 2009-04-14
I've used this command line tool "oggdec".

```
 sudo apt-get install vorbis-tools 
```

After its installed just do:
```
 oggdec -o file.wav file.ogg 
``` 

to convert your .ogg file to a wav file.

---

### Post by click4851 on 2009-04-14
batch encoding....the power of the command line

---

