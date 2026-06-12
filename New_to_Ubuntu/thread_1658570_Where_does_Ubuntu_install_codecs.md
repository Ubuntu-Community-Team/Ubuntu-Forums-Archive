---
title: "Where does Ubuntu install codecs?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by alayoyo on 2011-01-02
I have a program (subsonic) that during installation made a directory with links to codecs, but the location specified doesn't actually have them. I don't know where to point it to so it finds the codecs.

The codecs are on my system somewhere, i can play the files no problem. But the media players are so 'seamless' and 'just works' i can't figure out how they find the codec to play things. I'm also not sure what the file type will be for the codec, I need flac and monkey's audio specifically.

Thanks.

---

### Post by Frogs Hair on 2011-01-02
I use gstreamer plugins and they are stored in file system usr/lib . I hope that helps .

---

### Post by gordie69 on 2011-01-02
Try going to applications at the top left on desktop screen and goto ubuntu software center and type in codecs

---

### Post by AlphaLexman on 2011-01-02
I don't have the Monkey codecs on my system, but the flac codec is at:
```
/usr/lib/gstreamer-0.10/libgstflac.so
```
You can enter:
```
locate flac
```
from the command line and get a lot of info about the flac files on your system, the same could be done for monkey audio.

---

### Post by alayoyo on 2011-01-02
THanks. I think the flac was in /usr/bin . It did not have an extention, but nautilus recongnized it as an application and had a geary icon. I am still unsure where the other codec is, or how to find out since the file type is registered to the exail music application, not the codec specifically. Oh well, it probably would be easier to just make a folder and transcode them ahead.

---

### Post by wojox on 2011-01-02
Monkey Audio is APE and it's for Windows.

---

### Post by AlphaLexman on 2011-01-02
> **alayoyo said:**
> THanks. I think the flac was in /usr/bin.That is actually the binary executable file, not the codec...

> **alayoyo said:**
> Oh well, it probably would be easier to just make a folder and transcode them ahead.
What exactly are you trying to do?
Create flac files?
Convert flac files?
Play flac files?

---

### Post by alayoyo on 2011-01-03
> **wojox said:**
> Monkey Audio is APE and it's for Windows.

Yes, I started using ~5 years ago, while still using xp. I didn't realize it wasn't as usable on linux. Is flac the preferred lossless audio codec then?

> **AlphaLexman said:**
> That is actually the binary executable file, not the codec...

how are codecs then? On windows i looked for *.dll files to copy.

> What exactly are you trying to do?
Create flac files?
Convert flac files?
Play flac files?

I have my cds ripped to APE and a few flac as well that are on my desktop/server. I have subsonic application installed, which allows remote access to music files via my mobile. For large files like flac, i want to transcode them to mp3 which subsonic should be able to do. I can play play the files fine on my desktop, and ubuntu software center shows the right packages are installed.

---

