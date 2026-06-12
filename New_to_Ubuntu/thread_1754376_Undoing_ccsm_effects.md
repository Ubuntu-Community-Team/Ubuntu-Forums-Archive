---
title: "Undoing ccsm effects"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by make_markus on 2011-05-10
Hi!

I'm a total noob at linux so please stay with me.
Anyway i was trying to add some special effects using advanced desktop effects (cant remember exactly which ones i tried). And now when i start up ubuntu after login nothing shows up except a notifications that im on the internet or low battery power.. unless i use ubuntu (no effects).. How do i undo these effects or recover to a point where no changes were made. 

Help would be appreciated

---

### Post by synapsys on 2011-05-10
Try this command in a terminal

```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by wilee-nilee on 2011-05-10
> **make_markus said:**
> Hi!

I'm a total noob at linux so please stay with me.
Anyway i was trying to add some special effects using advanced desktop effects (cant remember exactly which ones i tried). And now when i start up ubuntu after login nothing shows up except a notifications that im on the internet or low battery power.. unless i use ubuntu (no effects).. How do i undo these effects or recover to a point where no changes were made. 

Help would be appreciated

There is a reset to default button for compiz.
[ATTACH]191724[/ATTACH]

You may need to bring up the config manager in unity so if you can get a terminal install the compiz manager if needed, and launch it from the terminal.

---

### Post by geazzy on 2011-05-10
> **synapsys said:**
> Try this command in a terminal

```
gconftool-2 --recursive-unset /apps/compiz
```

I tried this but there was no anything reaction in my ubuntu :D

---

### Post by wildmanne39 on 2011-05-10
I had that happen to me and I used unity --reset. After you boot try alt f2 if that does not bring up the terminal window try ctrl alt f2 and it should take you out to a terminal then enter unity --reset and that should reset unity and compiz.

---

