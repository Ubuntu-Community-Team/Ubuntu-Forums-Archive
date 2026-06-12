---
title: "Need to blacklist/disable pc speaker before..."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by dgrafix on 2009-02-03
i go nuts! ](*,)

Lol. i dont know why its still in use other than low level system debugging, but i HATE the system speaker with a vengeance. Every PC i own when running ubuntu emits that horrid uncontrollable beep when in editors, terminal etc.

I know abut modeprobe -r pcspkr but i need a permenent solution, before i arm myself with a screwdriver and rip it out wires and all._[U]_[/U]

---

### Post by spiderbatdad on 2009-02-03
try adding the line "blacklist pcspkr" to the file /etc/modprobe.d/blacklist

---

### Post by dgrafix on 2009-02-04
thx, ill try it :)

---

### Post by mªrty on 2009-02-09
an easier solution would be to type in terminal:
```
rmmod pcspkr
```
If you decide you miss it, this should re-load it:
```
modprobe pcspkr
```

---

