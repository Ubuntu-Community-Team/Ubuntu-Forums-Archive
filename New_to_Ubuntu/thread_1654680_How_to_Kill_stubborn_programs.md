---
title: "How to Kill stubborn programs"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by WhiskeySierraEcho on 2010-12-28
G'day, I was wondering if there is a set of key strokes that allows the killing of stubborn programs at all. If so could a kindly person please let me know.

Cheers

---

### Post by wojox on 2010-12-28
In a terminal run

```
top
```

Find the PID to the application, press K and enter it's #. ;)

---

### Post by laidback on 2010-12-28
I use System>Adiministration>System Monitor, which you can run and have in a window. Then under the Processes tab of System Monitor you will see the list of processes (programs) that are running. Highlight the one you want to stop and then press End Process.

---

### Post by s1baker on 2010-12-28
You also can right click in the top or bottom panel and select "add to panel", then scroll down and look for the "Force Quit" button, and add it to the panel.

---

### Post by WhiskeySierraEcho on 2010-12-28
Thankyou people, all three ways are useful. cheers :) 

wojox: it was fun trying to line up the PID with its name, as the list kept changing. lols

---

### Post by Sealbhach on 2010-12-28
htop is even better than top, have a play around with that too.
```

sudo apt-get install htop
```

.

---

### Post by WhiskeySierraEcho on 2010-12-28
Sealbhach, thanks also.

p.s. tried it, deff better as one can highlight a process and kill it, even if it moves in the list.

Cheers

---

