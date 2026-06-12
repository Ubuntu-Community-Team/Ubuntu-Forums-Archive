---
title: "How to disable the system beep (or bell) in Karmic"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by bvmou on 2009-10-31
I would love to completely shut off all system beeps (terminals, backspaces, etc) and cannot figure out how to do so in Karmic -- at one time it was an option in System > Sounds but the hardware interfaces have changed.  The pcspkr module seems no longer in use either.

How can I do this, short of using a hammer (which has crossed my mind)?

---

### Post by Xatolos on 2009-10-31
Unless I'm mis-understanding your question, it should be just System -> Preferences -> Sound and change the Sound Theme from Ubuntu (default) to No Sounds.
Hope that helps

---

### Post by bvmou on 2009-10-31
I have done that for the general sounds, but the internal speaker beeping persists -- for now I have found a solution for the two places where it annoyed me most,

1. In vim, in .vimrc, add "set visualbell"

2. In bash, in .bashrc, add "xset -b" ; I think the second option might have triggered some additional goodness since chrome is also no longer beeping.

Thanks Xatolos

---

### Post by LAI on 2009-10-31
bvmou, I've been annoyed by the same thing, and it looks like xset is exactly what I've been looking for. It disables the bell for the whole X session, and so isn't dependent on any particular WM or DM.

I'm going to have this run at X startup, rather than put it in .bashrc -- that way it won't run when, for example, I log in remotely. Or every time I open another shell.

So thanks to bvmou for pointing this out!

BTW: my hardware doesn't support changing the system bell volume, but some folks may want to try varying the pitch, volume or duration of the system bell instead of disabling it entirely:

```

$ xset b 10 200 150 # 10% volume, 200Hz, 150ms
$ xset b 50 400 100 # default settings

```

---

