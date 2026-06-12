---
title: "Turn off compiz without seeing the desktop?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by scared person on 2009-04-23
I managed to combine the right compiz effects so that the desktop is completely invisible.

How do I go about turning it off?

---

### Post by starcannon on 2009-04-23
Bring up the run dialogue box, I know you can't see whats going on but blind typing this should get you on track:

Alt+F2
type: metacity --replace
press: Enter

It should turn compiz off for you, and allow you to see what your doing so you can make appropriate adjustments to yoru compiz config settings.

---

### Post by kanikilu on 2009-04-23
If you can get to a terminal (or virtual terminal), I think this will disable compiz: ```
metacity --replace
```

// Edit - Too slow, see above ^ ;)

---

### Post by scared person on 2009-04-23
It Works!

I thought I going to have to reinstall 

Thanks a lot!

---

