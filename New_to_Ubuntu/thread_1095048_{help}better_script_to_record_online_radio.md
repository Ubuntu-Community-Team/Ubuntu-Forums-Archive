---
title: "{help}better script to record online radio"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by lolilolicon on 2009-03-13
Here is a simple script to record online radio to local disk.
```

#!/bin/bash
URL=http://64.62.252.130:8070
WORKDIR=/home/Gez/temp/mplayerdump

mplayer -dumpstream  $URL -dumpfile $WORKDIR/current.mp3

```
which is not satisfying enough...

I want to write a script to do this:
1.**one file per song**, NOT all stream recorded in one file called current.mp3
2.auto-rename "current.mp3" to "**$artist_$title.mp3**" everytime a song is ended

And when i run the script in terminal, i get the out put::
```

...
ICY Info: StreamTitle='Offspring, The - You're Gonna Go Far, Kid [Radio Edit]';StreamUrl='http://www.1.fm';
ICY Info: StreamTitle='AFI - The Leaving Song Pt. 2';StreamUrl='http://www.1.fm';

```
the point is, every time the stream is swithed to a new song, this output will add one line, containing "StreamTitle="
And i had no clue how to tail the terminal output directly,so i used >> to write all this output into a file called xxx,then i tried:
```

tail  xxx -n 1  | cut -d "'" -f 2 

```
the result is nice for me::
```

AFI - The Leaving Song Pt. 2

```
i think this could be used to rename the song.

and then i tried to write the script .... and with no result ..sad:(

i think the sign to song switch is: **one line added** to the terminal output, which could be described with "wc -l"
but i just have no way to do this::

while doing the stream recording  "mplayer -dumpstream  $URL -dumpfile $WORKDIR/current.mp3"
how to **monitor on the terminal output at the same time**, so as to tell mplayer to end this song at song switch??

i hope the answer is obvious to you.
help, please!

---

