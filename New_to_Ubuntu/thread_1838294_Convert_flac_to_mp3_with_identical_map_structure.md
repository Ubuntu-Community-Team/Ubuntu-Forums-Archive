---
title: "Convert flac to mp3 with identical map structure"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-09-03
Looking for a program that can convert flac to mp3 with tags and that replicate folder structure. I tried soundconverter problem is that it can't create the same map structure, the only thing that come close is to let Soundconverter create subfolders for every artist something that would have worked if it wasn't for soundtracks.

Let say that the path to a folder from the selected root folder is Rock/Iron Maiden/Album B/*.flac then would the location for the mp3 files be /some/path/Rock/Iron Maiden/Album B/*.flac

Soundtrack with SoundConverter
```

Music/Soundtrack A/Artist A - Song A.flac  --> path/Artist A - Soundtrack A/Artist A - Song A.mp3
Music/Soundtrack A/Artist B - Song B.flac  --> path/Artist B - Soundtrack A/Artist B - Song B.mp3
Music/Soundtrack A/Artist C - Song C.flac  --> path/Artist C - Soundtrack A/Artist C - Song C.mp3

```


EDIT: **Solution**
Found the solution in this perl script
[http://freshmeat.net/projects/flac2mp3/](http://freshmeat.net/projects/flac2mp3/)

---

### Post by Leshrac on 2011-09-03
Have you tried using ffmpeg?

something like:
ffmpeg -i song.flac -ab 196k -ac 2 -ar 48000 song.mp3
Should work for what you want, but I'm not entirely sure on whether it will carry over the tags though.

The folder structure could probably be preserved by writing a small shell script to automate the process.

That's the only way I can think of, other than doing it by hand.

---

### Post by stoian on 2012-02-14
look at this bash script, see if you can customize it to preserve/create the path you desire:

[http://pastebin.com/i50iQdeA](http://pastebin.com/i50iQdeA)

hope that helps.

---

