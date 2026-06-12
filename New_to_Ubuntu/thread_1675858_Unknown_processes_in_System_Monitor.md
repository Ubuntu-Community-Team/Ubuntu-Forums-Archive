---
title: "Unknown processes in System Monitor"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by thameera on 2011-01-26
I was checking my System monitor today when I noticed some processes that had no name. (See the screenshot attached). I checked again in about 10 minutes and they were gone. In another few minutes they appeared again.

Is this normal? Or is something malfunctioning?

---

### Post by sydbat on 2011-01-26
I don't know. What were you doing at the time (other than just checking your system monitor)?

---

### Post by thameera on 2011-01-26
Um.. there was Clementine playing music, Sound Converter doing some conversion, and I was browsing with Google Chrome. Also there was a dictionary (purple) and document viewer (evince) open.

---

### Post by Rubi1200 on 2011-01-26
Try this command in the terminal:

```
ps ax | grep <PID>
```

replacing PID with the actual process number. Since the process IDs are consecutive they are probably related to the same parent process.

---

### Post by thameera on 2011-01-26
Thanks, will check once the processes appear again. It seemed to appear and disappear, but not showing up anymore.

---

### Post by sydbat on 2011-01-26
I bet it had to do with the sound conversion. Take a music file and convert it with the system monitor open and see if it exhibits the same behaviour.

---

### Post by thameera on 2011-01-26
Yes! I tried converting the same songs again and they appeared again! Something to do with Sound Converter it is. Should be normal I guess.

---

### Post by Rubi1200 on 2011-01-26
Good to know. Now you can relax :-)

---

