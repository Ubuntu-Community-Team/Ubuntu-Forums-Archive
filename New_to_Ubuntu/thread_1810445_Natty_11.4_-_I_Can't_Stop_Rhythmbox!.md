---
title: "Natty 11.4 - I Can't Stop Rhythmbox!"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Andavane on 2011-07-23
I'm slowly getting used to Ubuntu 11.04 (on another machine).
I'm listening to an audiobook on Rhythmbox (I couldn't get banshee to play it) and it's playing away fine.

At my pause point I couldn't stop it when I exited (on earlier Ubuntu's I have right-clicked the icon in the top bar and quitted).

---

### Post by lmarmisa on 2011-07-23
Try Music -> Quit or Ctrl+Q.

Best regards,

Luis

---

### Post by e79 on 2011-07-23
Or from a terminal:

Step 1:
```
pidof rhythmbox
```Answer from your PC (example):

```
8736
```
This PID number will be random

```
kill 8736
```(here input the PID you found on step 1)

Hope this helps

---

