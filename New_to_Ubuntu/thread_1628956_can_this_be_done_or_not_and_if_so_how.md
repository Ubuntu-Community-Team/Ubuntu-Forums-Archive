---
title: "can this be done or not and if so how"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-23
here is an output from the terminal

ray@ray-desktop:~/Desktop$ cd  music
ray@ray-desktop:~/Desktop/music$ ls
christmas2pls   classical.pls    easy listening.pls  romantic.pls
christmas.pls   classicrock.pls  modern jazz.pls     smoothjazz.pls
classical1.pls  country.pls      newage.pls


is there a way to play lets say country.pls while still in the terminal mode and if so how/tks

---

### Post by nothingspecial on 2010-11-23
```
mplayer -really-quiet -playlist country.pls < /dev/null &
```

Don`t worry, the really quiet option suppresses output, it doesn`t play it really quiet.

---

### Post by searchfgold6789 on 2010-11-23
I would try 

[LIST]
[*][_**MPFC**_]("http://mpfc.sourceforge.net/")
[*][_**Cmus**_]("http://cmus.sourceforge.net/") (Really high ratings)
[*][_**MOC**_]("http://moc.daper.net/")
[*]_**[Mplayer]("http://www.mplayerhq.hu/")**_ (wide range of formats supported)
[/LIST]
Good luck.
 - search

---

### Post by rburkartjo on 2010-11-24
nothing tks. been using linux for 4 years and couldnt figure out how to do that. members on other forms had told me this couldnt be done

---

### Post by MrWES on 2010-11-24
Yah mplayer is pretty powerful from the command line. I have this crontab setup that pipes music to the baby's room 24/7; wife just turns the speakers on or off as needed.

```
@reboot /usr/bin/screen -dmS mplayer /usr/bin/mplayer -loop 0 -af volnorm /media/external/Music/Baby/*.mp3
```

Gotta love it!

~Bill

---

