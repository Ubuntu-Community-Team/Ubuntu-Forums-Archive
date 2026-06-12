---
title: "how to run an mp3 format using CLI..?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-13
[SIZE=3]***how can i run mp3 format through terminal code..?***[/SIZE]

---

### Post by arochester on 2010-09-13
Googled: ubuntu mp3 with cli

[http://ubuntuforums.org/showthread.php?t=513352](http://ubuntuforums.org/showthread.php?t=513352)
[http://www.go2linux.org/mpg123-linux-command-line-play-mp3-files](http://www.go2linux.org/mpg123-linux-command-line-play-mp3-files)
[http://www.linuxquestions.org/questions/linux-software-2/what-is-the-best-command-line-mp3-player-158950/](http://www.linuxquestions.org/questions/linux-software-2/what-is-the-best-command-line-mp3-player-158950/)

...more?

---

### Post by nothingspecial on 2010-09-13
```
sudo apt-get install mplayer-nogui ubuntu-restricted-extras
``````

mplayer /path/to/mp3/file
```

---

### Post by andrew.46 on 2010-09-24
Hi tajiknomi,

It would be well worth your while to have a look at a dedicated mp3 player with many options that has a lot of work done recently:

mpg123 - Fast console MPEG Audio Player and decoder library
[http://www.mpg123.de/](http://www.mpg123.de/)

Recent versions of MPlayer can be compiled against this and playback with:

```
mplayer -ac mpg123 filename
```

but it is sufficient unto itself as a cli player:

```

andrew@skamandros~/music/ftgws$ mpg123 --long-tag -v Revelation_21.mp3 
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 1.12.4; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes
Decoder: SSE

Playing MPEG stream 1 of 1: Revelation_21.mp3 ...

	Title:   A New Heaven
	Artist:  Lesley Garrett
	Album:   Lesley Garrett - The Singer
	Year:    2005
	Genre:   Classical
	Comment: ABC Classic FM broadcast

MPEG 1.0, Layer: III, Freq: 44100, mode: Joint-Stereo, modext: 0, BPF : 626
Channels: 2, copyright: No, original: Yes, CRC: No, emphasis: 0.
Bitrate: 192 kbit/s Extension value: 0
Frame# 13981 [    1], Time: 06:05.21 [00:00.02], RVA:   off, Vol: 100(100)
[6:05] Decoding of Revelation_21.mp3 finished.

```

Andrew

---

