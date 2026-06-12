---
title: "[SOLVED] convert mpg/vob to avi"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by lad3391 on 2008-12-29
im fairly nub at ubuntu, but not completely helpless, im running 8.10 on my dell insprion 6000 (laptop)

im looking to convert .vob files (from a dvd rip, which are basically mpg files that have been renamed .vob) to .avi

i have this command as listed by creative2 in another post

mencoder INPUTFILE -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT.avi


i THINK i understand the different parts of the command, and i can successfully run it, but the file gets pretty big, is there a way to convert and limit it by size, like 700mb, 1400mb etc?

---

### Post by RomeReactor on 2008-12-29
Hi. An easier way would be to try with [Handbrake]("http://handbrake.fr/") or AviDemux; it's in the repositories, look for it in Synaptic (System->Administration->Synaptic). Or to install from the terminal:
```
sudo aptitude install avidemux
```

You can then find it in 'Applications->Sound & Video->Avidemux'.

---

### Post by eagle416 on 2008-12-29
I use ffmpeg for all media conversion. simple text-based converter/editor.

```
sudo apt-get install ffmpeg
```

---

### Post by balaknair on 2008-12-29
Or the GUI frontend for ffmpeg--> WinFF :D

Linux spoils you for choices.

---

### Post by lad3391 on 2008-12-30
thanks for the choices! ill prolly try all of them see which i like

---

### Post by lad3391 on 2008-12-30
hmm it seemed to work kinda. i tried avidemux, and i thought i set it to 700mb but it came out as 3.6gb?

---

