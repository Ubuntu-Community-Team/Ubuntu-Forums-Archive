---
title: "[SOLVED] Refresh hardware detection?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by minsf on 2008-12-28
Ubuntu detects my cd drive correctly once in about five boots (other times lshw say status is open- though my tray is closed- doesnt get vendor name etc. and obviously i cant mount it then). until i fix this, can i ask ubuntu to re-detect the hardware, rathe than reboot?

---

### Post by blueridgedog on 2008-12-28
I don't know if this will work for you, but:

```
sudo /etc/init.d/hal restart
```

hal is the Hardware Abstraction Layer

---

### Post by minsf on 2008-12-30
Thanks. 
I need to research the hal daemon more, but this seems to be the correct way to refresh the hardware detection. 
It doesn't solve my cd mounting problem, but it does answer my above question- so thanks for your help- i will mark this thread as solved and i will start a new thread regarding my mounting problem later :)

---

