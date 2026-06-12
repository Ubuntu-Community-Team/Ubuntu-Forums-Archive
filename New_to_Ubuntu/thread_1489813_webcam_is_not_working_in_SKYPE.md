---
title: "webcam is not working in SKYPE"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by faisalijaz77 on 2010-05-21
My webcam is working in other applications but not working in skype. Can anyone help. I am using ubuntu

---

### Post by TeoBigusGeekus on 2010-05-21
Try to load skype via command line with this
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by faisalijaz77 on 2010-05-27
Sorry for replying you late.. I have still the same problem. I have A4tech PK-760E model webcam. Please help me to resolve this issue.


> **TeoBigusGeekus said:**
> Try to load skype via command line with this
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by Julita on 2010-05-27
Try this: LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

---

### Post by no2498 on 2010-05-27
and do not close the terminal

---

### Post by faisalijaz77 on 2010-06-12
Today my ubuntu recovered, for somehow file system get damage and i dont know how to recover. Again my apology to reply your late.

Great its working but whenever i close the terminal, the skype Quit/shutdown, how i am configure this.

pls also advice the way that skype run normally with webcam, Otherwise help me to create a terminal batch file so i can put at desktop to run the skype as I have to copy paste the code everytime.

regards
Faisal

---

