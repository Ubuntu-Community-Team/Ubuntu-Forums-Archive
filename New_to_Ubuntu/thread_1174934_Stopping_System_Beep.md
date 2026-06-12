---
title: "Stopping System Beep?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by thegodofguitar113 on 2009-05-31
Is such a said thing possible?

---

### Post by steeleyuk on 2009-05-31
When does the system beep occur?

You'll have to give us more information because deciphering things takes too much work.

---

### Post by kukibird1 on 2009-05-31
> **thegodofguitar113 said:**
> Is such a said thing possible?

[http://ubuntuforums.org/showthread.php?t=531781]("http://ubuntuforums.org/showthread.php?t=531781")

or in a terminal type 

echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist.conf

then 

sudo modprobe -r pcspkr

---

### Post by thegodofguitar113 on 2009-05-31
ok well i went to sounds through system and preferences. turned off all sounds... it seems that the only  time i get the beep is when i turn off my machine, which is still very annoying. and when i do what kuki bird says it isnt permanent it just seems to stop the beep for that shutdown only

---

### Post by steeleyuk on 2009-05-31
You're half way there then. It does this on Dell laptops for some reason.

What you need to do is blacklist the module. To do this, open a terminal and do:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

And at the bottom, type:

```
blacklist pcspkr
```

---

