---
title: "pipeing output into gedit?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Johnny420 on 2010-12-27
I am a Noob and I want to get to know some things about how my system works so I tried to redirect "help" and "set" into gedit so that i could have a txt copy for reference.
My understanding is that a command like

help | gedit

should work to output help into a gedit file for me to do with what I want.
all i get is gedit opens with nothing what am I doing wrong and are there any better ways to go about doing this.

copy and paste is for sissies

---

### Post by mcduck on 2010-12-27
sorry, that's not going to work, gedit doesn't accept text piped that way.

Why not just redirect the output directly into a text file?

```
somecommand > somefile.txt
```

---

### Post by Johnny420 on 2010-12-27
Thanx that worked

I guess I was wrong in thinking that gedit should accept piped output

---

