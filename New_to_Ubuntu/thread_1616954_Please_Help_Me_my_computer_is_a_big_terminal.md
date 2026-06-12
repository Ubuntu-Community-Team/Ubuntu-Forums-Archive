---
title: "Please Help Me my computer is a big terminal"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by ubunt12 on 2010-11-08
Hi im on a laptop here because my ubuntu has turned into a Terminal everytime i reboot, im just stuck on one big terminal.

please help me
thanks

---

### Post by JustinR on 2010-11-08
Does it give any errors? If not what if you do this?

When you log into the terminal, what happends when you type the command:
```

startx

```
then press Enter.

---

### Post by ubunt12 on 2010-11-08
no such file or directory (errno): unable to connect to x server
no such process (errno 3): server error

---

### Post by no2498 on 2010-11-08
or look at the sticky top of the General Help form

---

### Post by ubunt12 on 2010-11-08
might have to install again off cd

---

### Post by kalegs on 2010-11-08
Are you connected to internet?

---

### Post by JustinR on 2010-11-08
> **ubunt12 said:**
> no such file or directory (errno): unable to connect to x server
no such process (errno 3): server error

Can you login through the terminal and type:
```

sudo apt-get purge xserver-xorg-core
sudo apt-get install xserver-xorg-core

```

---

### Post by ubunt12 on 2010-11-08
ill try it now

---

### Post by ubunt12 on 2010-11-08
now should i reboot?

---

### Post by JustinR on 2010-11-08
> **ubunt12 said:**
> now should i reboot?

If the commands didn't give an error, then yes.

---

### Post by ubunt12 on 2010-11-08
its just doing the same thing ill just install it again thanks for your help though

---

### Post by ubunt12 on 2010-11-08
its doing the same thing ill just install it again thanks for your help though

---

