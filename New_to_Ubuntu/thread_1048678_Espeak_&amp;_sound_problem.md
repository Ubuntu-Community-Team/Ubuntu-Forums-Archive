---
title: "Espeak &amp; sound problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-01-23
Question:

I'm using espeak to give me the time when I play Quake3.
e.g. 
espeak -ven "time: It's 23:45."

Now because it needs to be modal, i call it with:
open espeak -ven "time: It's 23:45."

and to include it from the C programming language, I use:
system("open espeak -ven \"time: It's 23:45.\"");

That worked quite well for a while.
But then I compiled the new kernel
```

uname -r
2.6.29-rc2-custom

```

and as always when you do that, sound breakes.
So I recompiled the alsa drivers. 
Sound is back now, but I can't use espeak from quake anymore...
It just does not output any sound.

If I run espeak from the console while quake runs, espeak works.

The C code is correct, as it worked before kernel compilation, and I did not change it.


Anybody has an idea what that could be?
Lately I thougt I could pass it with pads:
open padsp espeak -ven "time: It's 23:45."
But that didn't help, too...

Anybody has an idea what that could be?

---

### Post by WitchCraft on 2009-01-24
bump.

---

### Post by WitchCraft on 2009-01-28
bump.

---

### Post by WitchCraft on 2009-02-07
Solved, after recompiling the alsa drivers, i also needed to recompile espeak.

And then it's also necessary to restart...! #-o

---

