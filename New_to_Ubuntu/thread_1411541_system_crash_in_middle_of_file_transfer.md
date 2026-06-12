---
title: "system crash in middle of file transfer"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Neofox85 on 2010-02-20
Hello ubuntu community I am a newbie running karmic 9.10 on a toshiba satellite L355D-s7901. I have been having problems with it overheating and shutting down since i started using ubuntu. A few days ago i was transfering a large amount of files to an external hard drive when it overheated and crashed in the middle of. Since then i haven't been able to bring up any folders from the places menu or the search menu it just shows the tab at the bottom that says opening downloads or whatever folder I'm opening then dissappears without any window popping up. I've scoured the forums looking for an answer which i found a fix for the overheating (hurray Ubuntu community) but still found nothing to fix the folder problem. If anybody could help would be much appreciated Thank you

---

### Post by cariboo on 2010-02-20
Boot from the Live cd, and once at the desktop, open an Applications->Accessories->Terminal and type:

```
sudo fsck -a /dev/sda
```

substitute you device label for the one in the example above.

---

### Post by Neofox85 on 2010-02-21
> **cariboo907 said:**
> Boot from the Live cd, and once at the desktop, open an Applications->Accessories->Terminal and type:

```
sudo fsck -a /dev/sda
```substitute you device label for the one in the example above.

Thank you for the quick reply. I put that through terminal and it came back with


fsck.ext2: device or resource busy while trying to open /dev/sda file system mounted or opened exclusivley by another program?


not sure if i did that right or if its still acting up please help thank you

---

