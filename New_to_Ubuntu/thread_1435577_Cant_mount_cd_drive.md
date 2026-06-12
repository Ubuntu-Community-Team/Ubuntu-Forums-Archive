---
title: "Cant mount cd drive"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by amnite on 2010-03-21
im using wubi/9.10. I have an HP computer with a built in cd/dvd drive. I tried uding it in ubuntu for the first time today to install diablo. when i double click on the drive i get this error msg. No mount object for mounted volume. And now it wont eject my cd. And when i try to eject via right click it says /dev/sr0 is mounted.

---

### Post by cariboo on 2010-03-21
To remove the cd from the drive, press Alt-F2 and type:

```
gksu eject /dev/sr0
```

Does the cd mount automagically when you insert it into the drive?

---

### Post by amnite on 2010-03-21
I restarted it and got it too eject and the waited to insert the cd till after ubuntu loaded and got it too work... But i have to use multiple cds to install and i cant just switch and hit ok i have to unmount after i switch and wait for it to remount. I got it figured out now but if you know could you explain y its done this way so if i have issues in the future i might be able to figure these issues out myself..

---

