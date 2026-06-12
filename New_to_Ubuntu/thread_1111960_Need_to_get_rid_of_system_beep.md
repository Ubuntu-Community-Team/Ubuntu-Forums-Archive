---
title: "Need to get rid of system beep"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by jose187 on 2009-03-31
I like my laptop to be quiet. I have disabled all the regular noises at start up etc.
But every time i log out / restart / shut down the computer, it emits this loud sharp BEEP!

I have tried a few things too, and none of the work. I managed to get rid of other system beeps, but no this one.

HELP PLEASE!

---

### Post by HermanAB on 2009-03-31
Sharpen pencil
Find electret beeper
Wham!
:)

---

### Post by Malalo on 2009-03-31
add the following line to "/etc/modprobe.d/blacklist" :

```
blacklist pcspkr
```

---

### Post by Achetar on 2009-03-31
You can also:
```

sudo apt-get remove beep;

```
But that could have severe unintended consequences (scripts crashing with 'Command not found' etc...)

---

### Post by BDNiner on 2009-03-31
Yeah i also have this issue. For some reason I don't have login or shutdown music anymore, just that annoying beep. I don't mind it during the POST since it serves a purpose but I don't need the PC to beep to tell me i have either started or shutdown the computer.

---

