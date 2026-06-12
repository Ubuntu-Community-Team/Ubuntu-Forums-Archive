---
title: "Where does sdb device mount to?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Clever_Username on 2010-08-05
When a device such as an mp3 player is plugged in via usb, where does it mount to? I thought all devices should show up in the /mnt folder, but I checked. There's nothing there. Even an 'ls -a" shows nothing. 
Don't get me wrong, everything is working fine. I'm able to access the mp3 player's files just fine through the desktop, I was just wondering how I would get to the files via command line.
Thanks so much in advance

---

### Post by oldos2er on 2010-08-05
Check /media

---

### Post by plucky on 2010-08-05
```
cat /etc/mtab
```

Good Luck

---

### Post by Clever_Username on 2010-08-07
Will do. Thank you so much!

---

