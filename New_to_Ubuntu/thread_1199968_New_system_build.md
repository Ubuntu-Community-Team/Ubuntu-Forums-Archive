---
title: "New system build"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by jrandolph on 2009-06-29
Im not sure if this is the right place for this, but here goes.
I am building a new box and it will have 8GB ram.
Do I need to install 64bit Ubuntu for it to recognize that amount of memory?

Thanks in advance

Jacob

---

### Post by Zzl1xndd on 2009-06-29
If you want to address that much ram then you will require a 64-bit Operating system.

---

### Post by LowSky on 2009-06-29
> **tweakedenigma said:**
> If you want to address that much ram then you will require a 64-bit Operating system.

Technically you are wrong. You can use a 32bit verison of Ubuntu, but you will need to enagle the PAE kernel to use the rest of you memory, using theis kernel patch will lower you performance a tiny bit.

64Bit is the best way to go, but 8GB is really a waste. I have 4 GB and I dont think it ever uses more than  1 gig playing HD video and internet pages and such.

---

### Post by Zzl1xndd on 2009-06-29
> **LowSky said:**
> Technically you are wrong. You can use a 32bit verison of Ubuntu, but you will need to enagle the PAE kernel to use the rest of you memory, using theis kernel patch will lower you performance a tiny bit.


Thanks for the info.

---

### Post by jrandolph on 2009-06-29
I understand that 8GB is quite a waste but I got a deal that I could not pass on so its all or none for bout $60 brand new 
I could put it into other boxes I have but for what reason you know.
I think the new box is going to dual boot with Vista (not my choice btw) and I know for a fact that I have to have 64bit Vista to recognize the ram

---

### Post by LowSky on 2009-06-29
pick up a RC copy of Windows 7 dont waste your time with Vista

---

### Post by jrandolph on 2009-06-29
RC copy?
I was just going to get Vista because I can get a free upgrade to 7

---

### Post by mikechant on 2009-06-30
With all that RAM sitting idle, I'm sure you could benefit from installing the 'preload' utility which loads frequently used programs before they are needed. Have a look at this:
[http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

You'll probably want to change the config file as described to get it to pre-load as much as possible.

As you can see from the performance tables, large applications like firefox and openoffice can load twice as fast.

---

### Post by LowSky on 2009-06-30
> **jrandolph said:**
> RC copy?
I was just going to get Vista because I can get a free upgrade to 7

windows "upgrades" never work really well. Better off using the RC and Buying 7 when it comes out.

---

### Post by Paqman on 2009-06-30
> **mikechant said:**
> With all that RAM sitting idle, I'm sure you could benefit from installing the 'preload' utility which loads frequently used programs before they are needed. Have a look at this:
[http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

You'll probably want to change the config file as described to get it to pre-load as much as possible.

As you can see from the performance tables, large applications like firefox and openoffice can load twice as fast.

I'd also start loading as much other stuff into RAM as possible, like /tmp and browser cache.

---

