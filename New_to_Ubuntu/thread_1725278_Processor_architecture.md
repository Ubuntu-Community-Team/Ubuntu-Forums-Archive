---
title: "Processor architecture?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Spyro543 on 2011-04-09
I'm wanting to get Debian for small CD's but it asks me for my processor architecture:

[IMG]http://i.imgur.com/COm4W.png[/IMG]

How can I find out my processor architecture in Xubuntu?

---

### Post by cottfcfan on 2011-04-09
I think you only have 1 gig of ram, so the i386 architecture would be the one to go for.

---

### Post by shad0w_walker on 2011-04-09
From what I can find of a quick googling of the N150 and the Atom N550 chip in it, you can go with I386 or AMD64 arches, either one should work fine for you as the N550 claims to be 64bit capable.

---

### Post by Spyro543 on 2011-04-09
Ok, that's what I thought.

I'll try that now.

---

### Post by tgm4883 on 2011-04-09
> **cottfcfan said:**
> I think you only have 1 gig of ram, so the i386 architecture would be the one to go for.

Amount of RAM has nothing to do with architecture.

---

### Post by cottfcfan on 2011-04-09
tgm4883.
I know, but with only 1 gig ram, I thought 64bit was pushing it a bit.

---

### Post by oldos2er on 2011-04-09
> **Spyro543 said:**
> How can I find out my processor architecture in Xubuntu?

```
cat /proc/cpuinfo
```

---

