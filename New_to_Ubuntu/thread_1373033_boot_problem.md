---
title: "boot problem"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by purvis on 2010-01-05
I want to begin by saying I am a total beginner here with no programming background. Yesterday I remove some applications I had installed and did not like. After I removed them and rebooted the computer it now comes to a screen that reads "Ubuntu is running in low-graphics mode". 
I am pretty certain that the computer itself is working fine because I have a flashdrive setup to be a clean boot of Ubuntu and it is working fine.

---

### Post by J V on 2010-01-05
If the applications have anything to do with it, which ones?

Otherwise it could be anything...

---

### Post by nothingspecial on 2010-01-05
Did you remove evolution?

You may have to boot into recovery mode and type

```
sudo apt-get install ubuntu-desktop
```

---

### Post by purvis on 2010-01-05
> **nothingspecial said:**
> Did you remove evolution?

You may have to boot into recovery mode and type

```
sudo apt-get install ubuntu-desktop
```

Thank you for this suggestion, it fixed the problem.

---

### Post by novateando on 2010-09-03
I have the same problem after removing evolution, how can restore ubuntu-desktop from ubuntu live-cd in recovery mode?

---

