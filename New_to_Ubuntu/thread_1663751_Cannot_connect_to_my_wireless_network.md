---
title: "Cannot connect to my wireless network"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by censor_speeqs on 2011-01-10
Hello, complete newb here. I know you guys prolly here these kinds of questions all the time and us newbs really appreciate your time! I just downloaded ubuntu 10.10 and so far i like it. However there is a problem, i cannot figure out how to connect to my wireless network. The first time i used it after downloading ubuntu my internet worked fine after i connected. But i restarted it and now it says wireless is disabled and i cannot find my router anymore. I am at a complete loss and would greatly appreciate your feedback!

---

### Post by mikewhatever on 2011-01-10
It might be obvious, but do make sure it's not turned off. If the witch is on, post the output of the following command:
```
sudo lshw -C network
```

It will show, hopefully, your networking hardware details.

---

### Post by censor_speeqs on 2011-01-10
the switch is not turned on and i refuses to :P

---

### Post by Hippytaff on 2011-01-10
Hi and Welcome!!
 
Have you tried enabling wireless by clicking on the wirless ion on the top right of the top panel?
 
Also as Mikewhatever says it would be useful to be able to see the output of commands like
```

lshw -c network

```
```

iwconfig

```

---

