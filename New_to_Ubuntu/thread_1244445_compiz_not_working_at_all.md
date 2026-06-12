---
title: "compiz not working at all"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by libihero on 2009-08-19
i used synaptic package manager to "completely remove" compiz and then i reinstalled it
when i reinstalled it, i have the program but none of the effects are working

---

### Post by LewRockwell on 2009-08-19
> **libihero said:**
> i used synaptic package manager to "completely remove" compiz and then i reinstalled it
when i reinstalled it, i have the program but none of the effects are working

should we assume you've attempted to activate it?

.

---

### Post by libihero on 2009-08-19
well i typed in "compiz --replace" in the terminal, and it activates it, but once i exit the terminal it turns back off....
how can i activate it permanently?

---

### Post by pedro3005 on 2009-08-19
System > Preferences > Startup Applications. Create a new entry, and input the command. It should run every boot now, but IDK if that is the most optimal solution.
Oh and you should be running that command on ALT F2 and not the terminal ;)

---

### Post by libihero on 2009-08-19
o ya i did do that, but when it starts up it has a little annoying flicker where the desktop reloads with the compiz activated
is there any better option?

---

### Post by themusicalduck on 2009-08-19
Go to System > Preferences > Appearance.

Go to Visual Effects and enable it from there.

If you want to do custom stuff with compiz, install simple-ccsm package first:

```
sudo apt-get install simple-ccsm
```

---

