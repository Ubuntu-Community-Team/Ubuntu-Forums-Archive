---
title: "Bash Scripting - Glob Magic?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by arekmenner on 2009-07-29
Hey, folks.

This is one of those situations where I have a little bash script that works just fine, but I feel like there should be a better way to do it.

The problem is transcoding flac to mp3. The command that I basically use is:

```
flac -d -c input.flac | lame -q 0 -b 192 --cbr - input.mp3
```
And I don't really need any recommendations on my encoding options :D

What I would like to know is if there is some magic way of propagating a glob through the pipe. Something like:

```
flac -d -c *.flac | lame -q 0 -b 192 --cbr - *.mp3
```
Such that the script would transcode every file to its own name in mp3.

Note that I do already have a script that does this by grepping for all flacs, then using basename and xargs to go into lame, but I'm just wondering if anyone knows of a better way. If there is no better way, then that's cool, too. Lots of love, everyone.

---

### Post by llamabr on 2009-07-29
At the end you say that you already have a script that does a forall $i ... basenames ...etc.  Post that script and tell us what it's not doing that you want it to do.

---

### Post by arekmenner on 2009-07-29
Heya
After taking about 5 minutes to think about it, I came up with the elegant solution that I wanted. One of those dufus moments, I guess. To whomever it may concern:

```
#!/bin/bash

for song in *.flac
do
        flac -d -c "$song" | lame -q 0 -b 192 --cbr - \
                "`basename \"$song\" .flac`.mp3"
done
```
It works great. Hooray bash!

---

