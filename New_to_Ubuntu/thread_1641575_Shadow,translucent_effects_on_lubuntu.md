---
title: "Shadow,translucent effects on lubuntu?"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by John Phang on 2010-12-09
Is there anyway to enable shadow and translucent window effect on lubuntu? (without using compiz) Because openbox has shadow effects on other distro isn't it?

---

### Post by cavalier911 on 2010-12-09
xcompmgr can do shadows and fade on some hardware. 
I tried with Lubuntu 10.04 LTS got errors and no effects.
Same hardware running Slitaz, a lighter weight openbox distro effects work.
slitaz has openbox menu with these commands to activate the effects.

Activate shadows
```
xcompmgr -c -r 10
```

Activate shadows/fade
```
xcompmgr -c -f -r 10
```

Stop effects
```
killall xcompmgr
```

---

### Post by John Phang on 2010-12-10
It worked! but after i restart it become normal again (no more shadow and fade effect) how can i set shadow and fade effect as default? (stick to my window without dissapearing after restart/shutdown).can you help me out please?

---

