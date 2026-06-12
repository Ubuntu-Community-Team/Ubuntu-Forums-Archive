---
title: "MicroSD card sets itself to read-only"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-05-25
Long story short, my MicroSD card for my phone is set to read-only and I cannot sync anything to it. It's rather annoying because it's my current media player and I don't see why it won't let me write anything to it.


All I get when I try to copy a file is "The destination is read-only."

Any suggestions?

---

### Post by taurus on 2009-05-25
Maybe you just need to remount it with the write option, umask=000.

Post the outputs of these two commands from a terminal.
```
sudo fdisk -l
df -h
```

---

### Post by mattbutsko on 2009-05-25
When I tried to mount it with write-ability, it was the same. 

I ended up fixing it by changing SD adapters. Not really a fix, but a bypass.

Thanks anyway.

---

