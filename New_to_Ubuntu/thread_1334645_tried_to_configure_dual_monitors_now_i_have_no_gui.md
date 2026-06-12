---
title: "tried to configure dual monitors now i have no gui"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-11-22
can someone please help me?  all i get is a black screen with a command prompt telling me usplash failed after fiddling with dual monitor setup

---

### Post by NoaHall on 2009-11-22
> **mamamia88 said:**
> can someone please help me?  all i get is a black screen with a command prompt telling me usplash failed after fiddling with dual monitor setup

Try running ```
sudo mv /etc/X11/xorg.conf /etc/X11/oldxorg.conf
```

---

### Post by mamamia88 on 2009-11-22
i get a response saying i am missing an operand

---

### Post by NoaHall on 2009-11-22
Hm. What happens when you run ```
startx
``` and then if that fails, ```
cat /etc/X11/xorg.conf
```

---

### Post by mamamia88 on 2009-11-22
start x doesn't work and that command issues a response saying no such file or directory

---

### Post by NoaHall on 2009-11-22
Hm. What graphics card are you using? What were you editing to set up dual?

---

### Post by mamamia88 on 2009-11-22
i am using a nvidia graphics chip in my laptop not sure which one.  i was just using the built in nvidia tool to set up dual monitors

---

### Post by NoaHall on 2009-11-22
Hm. Are you completely sure you are entering the commands in as I put? Try ```
ls /etc/X11
```

Use the EXACT case of letters I'm using.

---

### Post by mamamia88 on 2009-11-22
do i need the quotes?

---

### Post by NoaHall on 2009-11-22
> **mamamia88 said:**
> do i need the quotes?

No, no quotes.

---

### Post by mamamia88 on 2009-11-22
ok here goes nothing

---

### Post by mamamia88 on 2009-11-22
at least i have a gui now thanks now i have to figure out how to get driver working again and finally getting both monitors to work the way i want

---

### Post by NoaHall on 2009-11-22
> **mamamia88 said:**
> at least i have a gui now thanks now i have to figure out how to get driver working again and finally getting both monitors to work the way i want

Great, glad to hear it's working for you.

---

