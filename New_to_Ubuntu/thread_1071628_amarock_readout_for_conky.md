---
title: "amarock readout for conky?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-16
hi everybody.
does anyone know if its possible to get readouts from amarock in conky?
if so what might the script be?
that's all
thanks everyone
nigel

---

### Post by squaregoldfish on 2009-02-17
It is indeed possible. I have a script (attached) that I got from somewhere. I don't remember where it came from, so unfortunately I can't give credit. If you recognise the script as yours, please step forward!

It's very simple to use:

```
${execi 5 ~/.conky/amarok title}
```

Will add the title of the current song, updated every 5 seconds. Look in the script to see what other bits of info you can display.

Steve.

---

### Post by capnthommo on 2009-02-17
thanks squaregoldfish
that looks like what i want.
now i just have to set up my amarock to use mySQL instead of SQlite.  no worries.
cheers again
nigel

---

