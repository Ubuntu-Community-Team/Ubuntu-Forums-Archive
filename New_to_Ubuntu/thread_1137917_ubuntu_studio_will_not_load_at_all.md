---
title: "ubuntu studio will not load at all"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-04-26
basically as soon as i leave the grub screen i get this error message 

"clocksource tsc unstable delta = -109860236"

i dont understand how to resolve this

---

### Post by Bucky Ball on 2009-04-26
How did you install? From CD on clean disk/partition or add the Studio desktop and apps? If you are using nvidia graphics drivers and the rt kernel (realtime, low latency), Ubuntu Studio will usually not run at all. (There is a workaround).

---

### Post by PatrickMoore on 2009-04-26
> **Bucky Ball said:**
> How did you install? From CD on clean disk/partition or add the Studio desktop and apps? If you are using nvidia graphics drivers and the rt kernel (realtime, low latency), Ubuntu Studio will usually not run at all. (There is a workaround).

clean install on fresh hard disc space from a live dvd

---

### Post by PatrickMoore on 2009-04-26
ati radeon graphics. what could i do for a workaround?

---

### Post by PatrickMoore on 2009-04-26
seriously im lost here

---

### Post by steefjeqv on 2009-04-26
Hi,

Same problem here (radeon graphics-rv3xx).

Most of the time Ubuntu Studio boots fine (sometimes it hangs).

When it reaches the GDM (login), the screen gets garbled and the system freezes.

I'm going to try a fresh install this afternoon.

Greetings,
Steven

---

### Post by PatrickMoore on 2009-04-26
it may just be ubuntu studio. but i swear since the final release i have had nothing but trouble with my graphics card. normal ubuntu doesnt want to give me a driver for my card when i download it manually it wouldnt load ubuntu and now this. man makes me want to go back to the release candidate

---

### Post by steefjeqv on 2009-04-26
I'm going to give it up (for the moment).

Instead, I tried the beta3 version of 64Studio.
It's based on Ubuntu 8.04 with a 2.6.29-rt kernel.

Works fine over here.

Greetings,
Steven

---

### Post by Bucky Ball on 2009-04-26
I use Ubuntu Studio 8.04 lts with no problem, but I don´t use the nvidia drivers for my card with that.

---

