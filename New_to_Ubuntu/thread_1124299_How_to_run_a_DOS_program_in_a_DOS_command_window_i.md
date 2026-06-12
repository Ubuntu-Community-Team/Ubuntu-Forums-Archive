---
title: "How to run a DOS program in a DOS command window in Wine?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-04-13
I see that Wine has the CMD.EXE program. However, when I try to run it with Wine, nothing happens.

Is it possible to open a DOS command window under Wine, so that I can run an ancient DOS program?

---

### Post by anthonyp on 2009-04-13
Sorry paddy my post wont help but i too am curious if it is possible to install dos 6.22 in wine, and Windows 3.11.

---

### Post by Paddy Landau on 2009-04-13
> **anthonyp said:**
> Sorry paddy my post wont help but i too am curious if it is possible to install dos 6.22 in wine, and Windows 3.11.
You'd probably want to open a new thread on this, as it's unrelated to my question.

---

### Post by kpatz on 2009-04-13
I've been able to open the CMD.EXE in wine, you have to do it from a terminal, since it doesn't open a new window.

It probably won't run a lot of old DOS apps very well though.  You're better off using dosbox or Virtualbox running DOS in a VM.

---

### Post by PukingPenguin on 2009-04-13
> **anthonyp said:**
> Sorry paddy my post wont help but i too am curious if it is possible to install dos 6.22 in wine, and Windows 3.11.

I can't think of a reason DOS wouldn't work in Virtualbox....

---

### Post by Paddy Landau on 2009-04-13
> **kpatz said:**
> I've been able to open the CMD.EXE in wine, you have to do it from a terminal, since it doesn't open a new window.

It probably won't run a lot of old DOS apps very well though.  You're better off using dosbox or Virtualbox running DOS in a VM.
Cool, thanks for the advice! I'll give them a good try.

---

### Post by sirjoebob on 2009-04-13
> **Paddy Landau said:**
> I see that Wine has the CMD.EXE program. However, when I try to run it with Wine, nothing happens.

Is it possible to open a DOS command window under Wine, so that I can run an ancient DOS program?

I would recommend using dosbox. should be available in Synaptic/apt-get

[http://www.dosbox.com/information.php?page=0](http://www.dosbox.com/information.php?page=0)

---

### Post by CatKiller on 2009-04-13
If it's a game, then DOSBox is a good bet. If it's anything else, run DOSEmu instead.

---

### Post by llamabr on 2009-04-13
Dosbox will do what you want, maybe.

However, wine is very rarely the correct solution.  Instead, there's very likely a native application that will do what you want.

What, exactly, are you trying to do?  Probably it can be accomplished much more easily than you think.

---

### Post by Paddy Landau on 2009-04-13
> **sirjoebob said:**
> ... recommend using dosbox....

Thanks, dosbox did the trick. A little clunky, which is to be expected, but it works.

> **CatKiller said:**
> ... run DOSEmu instead.
DOSEmu gives me an error:
```
LOWRAM mmap: Invalid argument
Segmentation fault
```> **kpatz said:**
> I've been able to open the CMD.EXE in wine, you have to do it from a terminal, since it doesn't open a new window.

It probably won't run a lot of old DOS apps very well though.  You're better off using dosbox or Virtualbox running DOS in a VM.
You're right, CMD.EXE needs terminal to open. However, you were right again, the DOS program didn't work.

> **llamabr said:**
> What, exactly, are you trying to do?  Probably it can be accomplished much more easily than you think.
A blast from the past... The very [first computer adventure program]("http://en.wikipedia.org/wiki/Colossal_Cave_Adventure") (Colossal Cave Adventure) according to Wikipedia. I found [the DOS version]("http://www.rickadams.org/adventure/e_downloads.html"), with optional updates.

Thanks to everyone for your input.

---

