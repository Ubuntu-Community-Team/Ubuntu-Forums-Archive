---
title: "Launch to a specified desktop (not with compiz or devilspie)"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by High Camp on 2009-03-10
Hi All

I've been searching for an hour, I'm sure I could continue searching with different search terms and eventually find what I want. I'm wondering if there's a way to specify which desktop a program will launch on. First of all, I know and use Devilspie and Compiz to make constant rules. Basically, I have a list of 5 programs that I use for work so I've created a shell script to launch them all at the beginning of the day. I'm wondering if it's possible in that shell script to outline which desktop those programs launch on. I've noticed an option for display with Firefox and terminal (firefox --DISPLAY=1) but I've played with this and it doesn't work. I suspect it has something to do with X server, not what I'm looking for.

Help would be much appreciated and I hope I haven't been too vague here.

---

### Post by blueridgedog on 2009-03-11
To my knowledge this can't be done (this issue came up before in the forums).  I would love to be proved wrong as I have a need for a similar function.

---

### Post by Pithikos on 2010-10-12
just turn **firefox --DISPLAY=1 **into```
firefox --DISPLAY=:0.1
``` to display firefox on the secondary monitor or ```
 firefox --DISPLAY=:0.0
``` to display on the first one.
works for me :)

---

