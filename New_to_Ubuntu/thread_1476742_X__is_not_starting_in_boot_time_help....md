---
title: "X  is not starting in boot time help..."
date: 2010-05-08
forum: New to Ubuntu
---

### Post by heroidi on 2010-05-08
guys i have a problem X is not starting in boot time so i have to start it manually in tty1 or tty2 or tty3 or tty4 etc...

---

### Post by heroidi on 2010-05-08
I tried configuring the daemons in /etc/init.d and in bootup manager but its still not working please i need some help...

---

### Post by okplayer02 on 2010-05-08
what type of video card do you have? Have you installed the drivers for this card also? Just some things to answer.

---

### Post by heroidi on 2010-05-08
I can start X manually, its an Intel card and i have the drivers installed they are free drivers with free firmware X is not starting in boot time that is the problem

---

### Post by okplayer02 on 2010-05-08
check out the log for your x server show the details of it when you try to boot so we can say what is the error message.

to view your X server log

```
cat /var/log/kern.log | less
```

so you can view everything one page at a time

---

### Post by heroidi on 2010-05-10
I looked at my log file but its all normal nothing nada help...

---

