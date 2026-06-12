---
title: "OpenOffice and Firefox Slow to Respond"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by ergjoop3 on 2009-01-08
Hi

OpenOffice and Firefox are responding very slowly to scrolling and typing on my modern ThinkPad laptop. The pages essentially get stuck while scrolling and some letter appear only after a noticeable delay.

Why is this the case and how can I resolve these issues?

Thanks.

---

### Post by Liviu-Theodor on 2009-01-08
Please give some more information about your laptop, how much memory does it have, what kind of processor, how much memory is free.

---

### Post by gaffurabi on 2009-01-08
same problem here, too.

i have 
athlon 64, 3500+
3 gb ddr2 667mhz RAM
nvidia geforce 7300gs gpu
320 gb hdd 

i dont care much about open office but firefox is slow to response while i am browsing. strangely opera doesnt have that problem. so, kick the fox!

---

### Post by ergjoop3 on 2009-01-17
I have a 2007-era thinkpad: 2.6 GHz, 4 GB, 256 Mb graphics. What more information is needed?

---

### Post by beastrace91 on 2009-01-17
I notice this happening on my laptop as well from time to time, but I never noticed anything consistent about when it happens... (always seem kinda randomly)

System specs in my sig.

~Jeff

---

### Post by ergjoop3 on 2009-01-20
I also use Ubuntu 8.10

---

### Post by disappearedng on 2009-01-20
with firefox you should check for the latest updates, since firefox is known to have memory issues...

for openoffice it's a pretty big application, so it does take up a lot of memory, which will cause your computer to feel slow.

What I recommend you to do is to go to the terminal
type
```

top

```

look for these columns
```

 VIRT  RES  SHR

```

and see if firefox or open office gets out of hand (normally bigger than 200 - 300 mb ) depending on system

then what you could do is type (in the same terminal),
type
k (this is to kill),
the PID of firefox or whatever app.


**Example**

```

 5311 root      20   0  404m  51m  11m S    8  2.6  44:25.38 Xorg               

```

in my case I press k then 5311

---

### Post by jrusso2 on 2009-01-20
> **ergjoop3 said:**
> Hi

OpenOffice and Firefox are responding very slowly to scrolling and typing on my modern ThinkPad laptop. The pages essentially get stuck while scrolling and some letter appear only after a noticeable delay.

Why is this the case and how can I resolve these issues?

Thanks.

You need to check your CPU use and memory use.  It sounds like maybe your CPU use is high which causes those symptoms.  Run top to find out whats using so much cpu.

---

### Post by ergjoop3 on 2009-01-20
Ironically it looks like hard drive polling is high, not CPU and memory.

---

