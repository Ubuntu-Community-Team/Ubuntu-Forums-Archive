---
title: "Laptop mode and spindowns"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by yellowtuesday on 2009-08-19
Hi I recently enabled laptop mode by accident. I have a few questions about this. 

What does it mean when it says that it will make my hard drive spin down and how will this affect my hard drive life? How can I turn off laptop mode and how can I configure laptop mode so that it only turns on AC power. 

Also if its not asking too much what exactly does laptop mode do? I couldn't really understand the website. 

thanks in advance.

---

### Post by alexlafreniere on 2009-08-19
Well first off, are you using a laptop? To answer your question about what it does, laptop mode dims your screen brightness unless you force the brightness up and spins down your hard drive, meaning it will use your hard drive less often and stop it from spinning while not in use. I can't imagine this being bad for your drive, in fact I would assume it would extend it's life rather than shorten it. Think about it, using it less often means a longer life.

---

### Post by yellowtuesday on 2009-08-19
thanks for the reply. I was just worried about the spindowns [http://samwel.tk/laptop_mode/faq](http://samwel.tk/laptop_mode/faq) . 

Also do you know how to turn it on or off or have it turn on only when I'm on battery power? or is that the default.

---

### Post by alexlafreniere on 2009-08-19
Laptop mode should only turn on when you are not connected to AC power.

---

### Post by eldragon on 2009-08-19
> **alexlafreniere said:**
> Well first off, are you using a laptop? To answer your question about what it does, laptop mode dims your screen brightness unless you force the brightness up and spins down your hard drive, meaning it will use your hard drive less often and stop it from spinning while not in use. I can't imagine this being bad for your drive, in fact I would assume it would extend it's life rather than shorten it. Think about it, using it less often means a longer life.

laptop mode does a lot more than that. check its man page for an in depth of what you can set it to do when on ac / battery.

another misconception, spinning down the drive actually shortens the hdd's life span since it stresses the mechanics inside. unless its constantly being done, dont worry about it, it will make your battery last longer.
there even was a long discussion on the subject due to certain manufacturers shipping HDD's with a short timeout within writes which would make a hdd last less than 2 years. (aka spinning down too often).

advice: if its not a laptop, dont enable laptop mode.
if its a laptop, and you plan on using it on battery a lot, then i would enable it, amd make it as agressive as i can (this would keep the hdd powered down most of the time, but a power outage like battery running out will make you lose more work).
if you dont use your laptop with a battery for long periods of time, dont set it up, its annoying to wait for the hdd to spin up when you need to read something off it.

hope i cleared some stuff up

---

