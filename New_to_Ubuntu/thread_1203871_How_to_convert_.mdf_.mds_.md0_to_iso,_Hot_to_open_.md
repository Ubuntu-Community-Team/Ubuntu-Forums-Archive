---
title: "How to convert .mdf .mds .md0 to iso, Hot to open .mdf .mds .md0 alchohol files"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by powel212 on 2009-07-03
This is what I have found for dealing with .mdf .mds .md0 alcohol 120% files.

Usually if I get these files they contain videos so this post is specifically for dealing with these kinds of files in Ubuntu.

Option 1:
Drag the whole group of .mdf files into avidemux. Avidemux is awesome and will most times recognize these files as mpg which they are. Once in Avidemux just chose video encoding of your choice. I use "copy" as it is super fast but you end up with larger flies.

Option 2:
This should work for both video and data files. But I have only tested it on video files.
In a terminal type;
```
cat /folder/file.md0 /folder/file.md1 /folder/file.md2 > /folder/file.iso 
```
or
```
cat /folder/file.md0 /folder/file.md1 /folder/file.md2 > /folder/file.mpg
```

This is also a very fast way to convert the Alcohol files into .iso

This has been a post to help newcomers deal with a problem that took me a while to figure out.

I used to use Daemon Tools lite in a virtualbox running an XP guest which also works very well, (Daemon tools is awesome, Kudos), but this method takes a little longer.

That's it.

Enjoy

Powel

---

### Post by nhasian on 2009-07-04
stupid proprietary disc image formats.  they are really not necessary at all as we have standard open source disc image formats.  anyway, you can convert them with [acetoneiso]("http://www.acetoneteam.org/")

---

### Post by powel212 on 2009-07-04
> stupid proprietary disc image formats. they are really not necessary at all

+1 and Ah-Men to that.

P

---

