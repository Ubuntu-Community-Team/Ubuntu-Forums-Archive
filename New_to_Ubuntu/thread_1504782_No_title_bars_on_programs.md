---
title: "No title bars on programs"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by gordonflan on 2010-06-08
I have just updated two machines from Ubuntu 9 to 10.04LTS. One works perfectly, the other (done exactly the same way) starts with a cross for the cursor, and no title bars on any programs. System/preferences/appearance/visual effects on the duff machine starts with None as the option. Changing this to Normal puts everything right until I switch off and reboot. Then I'm back to the problem. The save for the changes does not seem to be permanent. Can anyone point me to where to look to put this right please.

---

### Post by skompier on 2010-06-09
Sounds like a window manager problem. When the titles disappear again, open a terminal and type...

```
metacity --replace
```

---

### Post by f.zacka on 2010-06-12
Check your startup applications for Devilspie application and disable if present. This was set on mine to (Maximise) (undecorate) (focus). Don't know where it came from, Some update maybe????

---

### Post by gordonflan on 2010-06-17
:confused: No more success than my own effort. Yes metacity fix restored the title bar to that program but wasn't global as my fix was (preferences/appearance/visual effects to nromal from none) But when I have to switch off I have to go through this again. It must be a text file somewhere which needs editing. What is the window manager in 10.04 called?

---

### Post by cap10Ibraim on 2010-06-17
did you have compizConfig installed before the upgrade ?

---

### Post by RJ12 on 2010-06-18
> **gordonflan said:**
> :confused: No more success than my own effort. Yes metacity fix restored the title bar to that program but wasn't global as my fix was (preferences/appearance/visual effects to nromal from none) But when I have to switch off I have to go through this again. It must be a text file somewhere which needs editing. What is the window manager in 10.04 called?

Metacity (GNOME / Ubuntu)
KWin (KDE / Kubuntu)

---

