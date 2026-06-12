---
title: "Ubuntu in VirtualBox"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by luckyvictor on 2010-09-12
Hi all

I am a beginner on using Ubuntu. I am in fact using windows 7, and run Ubuntu using VirtualBox.

Now I am facing a problem, I connect my phone to the computer, and I would like my virtual Ubuntu to detect it and be able to read the storage in my phone as well, how do I do it please?

---

### Post by JustinR on 2010-09-12
First, you need to install VirtualBox Guest Additions in Ubuntu (this will allow you to have USB support - which is what your phone needs).

Follow this to install guest additions on Ubuntu:
[http://www.virtualbox.org/manual/ch04.html#id2658274](http://www.virtualbox.org/manual/ch04.html#id2658274)

Then, after you have restarted Ubuntu, go to (VirtualBox Menu) Devices > USB Devices > {Whatever your phone is called}.

Then Ubuntu should recognize it. I would recommend using Bitpim to extract data off of it.

---

### Post by TNT1 on 2010-09-12
> **JustinR said:**
> First, you need to install VirtualBox Guest Additions in Ubuntu (this will allow you to have USB support - which is what your phone needs).

Follow this to install guest additions on Ubuntu:
[http://www.virtualbox.org/manual/ch04.html#id2658274](http://www.virtualbox.org/manual/ch04.html#id2658274)

Then, after you have restarted Ubuntu, go to (VirtualBox Menu) Devices > USB Devices > {Whatever your phone is called}.

Then Ubuntu should recognize it. I would recommend using Bitpim to extract data off of it.

Guest additions alone is not the answer. if you have OSE license, you wont have USB support, and you will need to change virtualbox to the PUEL version.

---

### Post by Elfy on 2010-09-12
> **TNT1 said:**
> Guest additions alone is not the answer. if you have OSE license, you wont have USB support, and you will need to change virtualbox to the PUEL version.

I think that would only be for linux versions - the OP is running ubuntu in a VM running in windows :)

---

### Post by TNT1 on 2010-09-12
> **forestpiskie said:**
> I think that would only be for linux versions - the OP is running ubuntu in a VM running in windows :)

Ah, right, sorry. It's been a long day.

---

