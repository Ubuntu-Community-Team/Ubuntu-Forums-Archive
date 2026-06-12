---
title: "Twonky Install"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by skinjim on 2010-08-23
As you may be able to tell from this post I really am a complete newbie when it comes to all things Linux. One thing I've noticed so far is that all the tutorials I've found assume that you already know what you're doing. And I don't. All I need to know is exactly how to install Twonky Server. I've downloaded a file called tonkymedia-i386-glibc-2.2.5-6.0.1.sh and now I have no idea what I'm supposed to do with it. I'm sure this is painfully simple but it's driving me mad so if any of you kind people can help I'd really appreciate it.

---

### Post by kbless7 on 2010-08-23
put the file on your desktop then run

```
cd ~/Desktop
sh tonkymedia-i386-glibc-2.2.5-6.0.1.sh
```

---

### Post by skinjim on 2010-08-23
> **kbless7 said:**
> put the file on your desktop then run

```
cd ~/Desktop
sh tonkymedia-i386-glibc-2.2.5-6.0.1.sh
```

I've done that and this is the message I get:
mkdir: cannot create directory `/usr/local/twonkymedia': Permission denied

Any thoughts? Thanks for replying by the way.

---

### Post by Kobalt on 2010-08-23
> **skinjim said:**
> Permission denied
Try to run the script with *sudo* before the afore mentionned command line.

---

### Post by kbless7 on 2010-08-23
```
cd ~/Desktop
sudo sh tonkymedia-i386-glibc-2.2.5-6.0.1.sh
```

---

### Post by skinjim on 2010-08-23
Brilliant! Thanks so much; now I just have to figure out how to use it :D

---

