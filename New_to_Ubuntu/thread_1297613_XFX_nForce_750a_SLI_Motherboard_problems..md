---
title: "XFX nForce 750a SLI Motherboard problems."
date: 2009-10-21
forum: New to Ubuntu
---

### Post by ShadeMK on 2009-10-21
Hello, I am new to Ubuntu and having some problems. Whenever I try to install Ubuntu and boot into it, nothing happens. It will ask me if I want to use Windows or Ubuntu, and I pick Ubuntu. Then it just goes to a screen with a flashing _ and thats it. I cannot type or anything and am forced to reboot. Can anyone help?

I have a XFX nForce 750a SLI Motherboard and I believe that is the source of my problems, maybe someone knows what to do.

---

### Post by edin9 on 2009-10-21
> **ShadeMK said:**
> Hello, I am new to Ubuntu and having some problems. Whenever I try to install Ubuntu and boot into it, nothing happens. It will ask me if I want to use Windows or Ubuntu, and I pick Ubuntu. Then it just goes to a screen with a flashing _ and thats it. I cannot type or anything and am forced to reboot. Can anyone help?

I have a XFX nForce 750a SLI Motherboard and I believe that is the source of my problems, maybe someone knows what to do.

Do you have cards in SLi?

---

### Post by ShadeMK on 2009-10-22
> **edin9 said:**
> Do you have cards in SLi?

I do not.

---

### Post by ShadeMK on 2009-10-22
Is there anymore information I can help you guys with? Please just ask.

---

### Post by RJARRRPCGP on 2009-10-23
A blinking cursor = sounds like corrupted boot information. (usually a corrupted boot loader!)

---

### Post by ShadeMK on 2009-10-23
> **RJARRRPCGP said:**
> A blinking cursor = sounds like corrupted boot information. (usually a corrupted boot loader!)

How would I go about fixing that? Sorry, I'm a noob when it comes to things like this.

---

### Post by ShadeMK on 2009-10-23
> **RJARRRPCGP said:**
> A blinking cursor = sounds like corrupted boot information. (usually a corrupted boot loader!)

I googled this and got no solid answer. Maybe someone here could point me in the right direction?

---

### Post by lkraemer on 2009-10-24
Will your system boot properly from a LiveCD of the Version you are installing?
What Version x.xx?  Does the LiveCD test good when you did
the MD5SUM test to VERIFY the ISO before Burning?  Did you burn as
DAO and at a SLOW speed?  You can always try another Burn on a different
CDRW media as a test.

Is your system installed as a Dual Boot with Windows xxxx?
If so, will Windows boot properly?  Did GRUB write to the MBR of the
Windows install?

Did you try installing the alternate Version if the regular version didn't
run properly after being installed?

lk

---

