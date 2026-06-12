---
title: "ogg to mp3"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Scott A on 2009-05-10
Hello, 

thanks for all the help 1.5 years ago when i first got started with ubuntu!

How do I make ogg files into mp3 files?

Thanks, 

Scott A

[email]jasa711@yahoo.com[/email]

---

### Post by metallicamike on 2009-05-10
Get sound converter from add/remove, then edit->preferences and make the output mp3

---

### Post by nhasian on 2009-05-10
there's probably a bunch of different ways to do it.  You could easily do it with audacity.

```
sudo apt-get install audacity
```

you'll need to also add the lamemp3 plugin to export to mp3.

---

### Post by andrew.46 on 2009-05-11
Hi Scott,

> **Scott A said:**
> How do I make ogg files into mp3 files?

The hands-on way with the command line may look a little ugly but it can *easily* be scripted:

```
mplayer myfile.ogg -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
lame --preset fast standard output.wav myfile.mp3
```

and there are many, many opportunities to fine-tune the output.

Andrew

---

### Post by Linux_Kid66 on 2009-05-11
You could use Media-convert.com, but it wasn't working this morning when i tried, probably updating.
Audacity is another option, or google it.

---

### Post by Roadbloc on 2009-05-11
Get Konverter. Availaible on Add/Remove.

---

### Post by kpkeerthi on 2009-05-11
Or try [soundconverter]("http://soundconverter.berlios.de/"). Install using synaptic.

---

