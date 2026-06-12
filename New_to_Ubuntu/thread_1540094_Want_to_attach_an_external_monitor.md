---
title: "Want to attach an external monitor"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by rkakkar on 2010-07-27
Hi,

I want to attach an external monitor to my laptop. I have a HP Compaq 6720s. Currently the maximum resolution of my laptop screen is 1280x800. The monitor I want to attach has a maximum resolution of 1920x1080. Will it work at this resolution? I mean it won't be limited by the inbuilt graphics card in my laptop, right?

Also, what if I want to switch off my laptop screen and only use my external monitor each time without having to set it manually - how can I do so?

---

### Post by TeoBigusGeekus on 2010-07-27
It *will* be limited to the max resolution of your graphics card, sorry.

---

### Post by rkakkar on 2010-07-27
> **TeoBigusGeekus said:**
> It *will* be limited to the max resolution of your graphics card, sorry.

How can I confirm, *before* purchasing the monitor?

---

### Post by clhsharky on 2010-07-27
rkakkar

I don't  think your questions can be answered with out knowing your chip first.
```
lspci | grep VGA
```

Sharky

---

### Post by rkakkar on 2010-07-28
> **clhsharky said:**
> rkakkar

I don't  think your questions can be answered with out knowing your chip first.
```
lspci | grep VGA
```

Sharky

I don't have Ubuntu as of yet, so can't run the command. But I looked up my laptop specs on the internet and found out I have a Intel Graphics Media Accelerator X3100. Would that help?

---

### Post by TeoBigusGeekus on 2010-07-28
According to google, your graphics card does support 1920x1080.
But I wouldn't hold my breath for HD movies playing smoothly on Ubuntu...

---

