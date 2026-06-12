---
title: "how to get other users env vars?"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by nerdy_kid on 2009-11-20
hey all, so heres what i need:

i currently ssh to a pc running a graphical session as a different user.
i need to get the $DISPLAY of the said graphical session (after sudoing into the user who is running X )
so i can play mean pranks on my sister while she is trying to listen to music. :lolflag:
[edit] i do have more serious reasons for posting this


is there a way to do this?

---

### Post by nerdy_kid on 2009-11-20
edit never mind

---

### Post by ibuclaw on 2009-11-20
Threads merged. Please don't cross post next time.

As for your question... pranks aren't very nice. You should be a better brother. ;)

Something that might lead you in the right direction though.
```
who
```
and for making a variable global
```
export DISPLAY
```

Regards
Iain

---

### Post by nerdy_kid on 2009-11-20
yeah sorry about that, i posted in the general help, but then decided i wanted in the other one...didnt know about cross posting sorry :(

my sister still talks to me so it cant be to bad ;)

thanks!  i didnt realize that 'who' printed the consoles the sessions were running on...perfect!

---

### Post by bodhi.zazen on 2009-11-20
For the lazy typer ;

s/who/w

```
w
```

---

### Post by nerdy_kid on 2009-11-20
> **bodhi.zazen said:**
> For the lazy typer ;

s/who/w

```
w
```
ahhh even better!

---

### Post by ibuclaw on 2009-11-21
> **bodhi.zazen said:**
> For the lazy typer ;

s/who/w

```
w
```

That is pretty cool, I must admit in awe. ;)

---

