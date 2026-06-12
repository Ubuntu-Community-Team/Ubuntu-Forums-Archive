---
title: "Wubi and Windows running at same time?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Sholto on 2010-06-12
I have a dual boot system running on one of my PC's now i.e. Ubuntu running outside Windows. I would like to be able to run both simultaneously, i.e. to open, say, a Linux console/terminal window from inside Windows.
Would a Wubi installation allow me to do this, or would it also require me to make a boot selection at startup so I would go into one or the other, not both?

---

### Post by an0dos on 2010-06-12
You should look into installing Virtualbox in either Windows or Linux and running the other OS in a Virtual Machine. Virtualbox has some interesting OS integration features if you use the "Guest Additions". Overall it is a very useful tool.

---

### Post by lovinglinux on 2010-06-12
> **Sholto said:**
> I have a dual boot system running on one of my PC's now i.e. Ubuntu running outside Windows. I would like to be able to run both simultaneously, i.e. to open, say, a Linux console/terminal window from inside Windows.
Would a Wubi installation allow me to do this, or would it also require me to make a boot selection at startup so I would go into one or the other, not both?

Wubi works exactly like a dual-boot, except for the fact that the file system is stored on a virtual partition inside Windows file system. So, no, you won't be able to launch anything from Linux while using Windows and vice versa. You need a Virtual Machine to do that, as already suggested.

---

### Post by tom.swartz07 on 2010-06-12
Or you could try this: [http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

Its a portable version of Ubuntu that runs like a program in windows.

---

### Post by lovinglinux on 2010-06-12
> **tom.swartz07 said:**
> Or you could try this: [http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

Its a portable version of Ubuntu that runs like a program in windows.

Cool.

---

### Post by tom.swartz07 on 2010-06-13
> **lovinglinux said:**
> Cool.

Danke.

Love me some Lifehacker

---

### Post by Sholto on 2010-06-15
Thanks guys.  Sorry I didn't reply before - it was a holiday weekend in Oz, and my son's birthday to boot.
I tried the portable Ubuntu.  It seemed a fantastic idea, but it doesn't seem to work.  I have posted a new thread about this.

---

