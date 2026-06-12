---
title: "Laptop fan runs on high speed constantly under Karmic Koala"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by bilekbp on 2009-11-12
Hello, I am having problems with my Compaq Presario since I upgraded Jaunty to Karmic Koala (64-bit). Once I upgraded my laptop fan runs at high speed continuously. It never drops its speed down, regardless of the load on the processor. In the past with Jaunty (and Intrepid beforehand) the fan would only run at high speeds when under heavy loads, and while the OS booted.

To be clear, I was running Jaunty Jackalope 9.04 64-bit version and upgraded to Karmic Koala 9.10 (by clicking the distribution upgrade button).

Can anyone help me understand why the fan is doing this, and how to solve it?

Thanks!

---

### Post by coldReactive on 2009-11-12
sudo apt-get install hardinfo

See if anything in hardinfo is screwy.

If sensors don't show, sudo apt-get install lm-sensors, run sudo sensors-detect afterward.

---

### Post by bilekbp on 2009-11-12
Hi, thanks for your help - when I run sudo sensors-detect, it is asking me if things are built into my kernel. How do I know if they are?

The first one is "i2c-i801".

Thanks!

---

### Post by coldReactive on 2009-11-12
> **bilekbp said:**
> Hi, thanks for your help - when I run sudo sensors-detect, it is asking me if things are built into my kernel. How do I know if they are?

The first one is "i2c-i801".

Thanks!

Just type yes to everything, it's what I did :|

---

### Post by bilekbp on 2009-11-12
Ok, done, and I don't see any problems in hardinfo...

---

### Post by bilekbp on 2009-11-13
Hi, sorry, I should be more clear: I did everything as instructed, said "yes" to everything, and while I did not get any error messages and I see nothing screwy in hardinfo, my fan is still spinning far faster than it ever did (except when under heavy loads) under Jaunty.

Any ideas?

Thanks!

---

### Post by Jugney on 2009-11-17
I am having the same issue on a fairly fresh install of Karmic on an HP dv6000 laptop. Doesn't do it if I boot into Vista. It's getting pretty annoying, so I would also like to see a solution to this. Did you get anywhere with this?

Jugney

---

