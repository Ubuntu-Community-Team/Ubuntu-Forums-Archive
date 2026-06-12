---
title: "&quot;could not enable visual effects&quot;"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-11-19
I had some graphics card problems which are now sorted but i am still unable to enable the Extra section in visual effects. The graphics driver is enabled and stuff, not sure what's wrong.

---

### Post by theozzlives on 2010-11-19
We need more info about your graphics card. Chipset, RAM, etc.

---

### Post by Rave Gloves on 2010-11-19
```
andrew@andrew-R610:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
```

Ram is 2gb, it's always worked for me, just today everything has just mucked up..

---

### Post by theozzlives on 2010-11-19
You have THE card. try pressing ALT+F2 and type:
```
compiz --replace
```

---

### Post by Rave Gloves on 2010-11-19
> **theozzlives said:**
> You have THE card. try pressing ALT+F2 and type:
```
compiz --replace
```

Tried it, it takes me to my visual effects and when i select extra it just makes my screen flicker and it goes back to none

---

### Post by theozzlives on 2010-11-19
try adding that to your startup programs, then reboot.

---

### Post by Rave Gloves on 2010-11-19
> **theozzlives said:**
> try adding that to your startup programs, then reboot.

That hasn't worked ether :/ im losing hope, i may have to do a fresh install.

---

