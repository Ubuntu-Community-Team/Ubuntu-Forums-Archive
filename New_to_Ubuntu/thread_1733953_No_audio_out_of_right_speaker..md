---
title: "No audio out of right speaker."
date: 2011-04-19
forum: New to Ubuntu
---

### Post by itguy1985 on 2011-04-19
The balance is in the middle. This only happens when logged into ubuntu. If I log into any other os, or use any other device it works fine.

---

### Post by corrytonapple on 2011-05-15
Did you try moving the slider more towards the Right then?  If it does not work, has it ever worked?  Does it work in Windows?

---

### Post by Johnley on 2011-05-15
try restarting pulseaudio

```
killall pulseaudio
```

and then start it with

```
pulseaudio
```

as user, not as root.

---

