---
title: "Conky Music Player (VLC)?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Codix121 on 2009-09-09
Anyone know where I can get a script to show what I'm currently playing,
I've seen it before with MPD but MPD isn't working for me, any idea on how I can get Conky to work with VLC on now playing, etc? I'd appreciate it thanks!

---

### Post by wildman4god on 2009-09-09
as far as I can tell their is no offical way of doing it, however [here]("http://forum.videolan.org/viewtopic.php?f=13&t=41938") is a link to a vlc forum that by the end of page one they find a way of doing it if you don't mind manually editing the conky rc file, the code is on the forum so you can just cut and paste it.

---

### Post by L31N on 2012-12-03
Hi all, 
I have written a litte script which uses the window-title of you vlc.  the script looks like this:

```
#!/bin/bash

line=$(exec xlsclients -l | grep "VLC media player" | cut -c -9 --complement)
line=${line%" - VLC media player"}
echo $line;

```It reads the window-title and than it formats the string,
so at the end it returns only the track vlc is actually playing.

in your conkyrc-file you can add it with following line:

```
${execi 1 "FILEPATH_TO_THE_SCRIPT_ABOVE./script.sh}
```(in this case the script is called script.sh, the 1 defines an interval of 1 sec)

i hope this post will be useful for everyone who wants to include the vlc-tracknames into conky.

L§!N

---

### Post by foxanthony on 2013-10-20
This can be put directly in conky w/o need for shell script:
```
${exec xlsclients -l | grep "VLC media player" | cut -c -9 --complement | sed -e "s/^.*: //g" \
| sed -e ':a;N;$!ba;s/\n/ - /g' | head -c -19 | sed 's/\(.\{,100\}\).*/\1/'}
```

I honestly don't understand sed, I hacked this together from various posts around the 'net, but the "100" is the limit I set for the length of text that will show.

---

### Post by oldos2er on 2013-10-21
foxanthony, please start a new thread; this one's quite old.

Closed.

---

