---
title: "Does Compiz Cause Hangs?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-18
Hi! I've been using Jaunty without a hitch since it was released until I decided to get updates just a couple of days ago. Just a couple of hours since I installed the updates I got my first system hang (no keyboard/mouse response no RSEIUB only option is hard restart). From then on I'm getting sporadic system hangs.

I went to the ubuntu IRC chan to ask about this and one suggested that it could be compiz. Is this really the case? Right now I'm running metacity and I'm not experiencing any problem. Does anyone have this same problem? Can anyone suggest a fix?

---

### Post by Dan_Dranath999 on 2009-05-18
Compiz has caused more than 1 stability issue

---

### Post by mvalviar on 2009-05-18
> **Dan_Dranath999 said:**
> Compiz has caused more than 1 stability issue

How come its so severe this time. I remember having compiz issues before but it doesn't bring the whole system down, compiz simply dies.

---

### Post by philinux on 2009-05-18
I assume you've rebooted.

---

### Post by mvalviar on 2009-05-18
> **philinux said:**
> I assume you've rebooted.
Its sporadic. My PC is not acting up now. Maybe because I have compiz off or maybe its just not happening now.

---

### Post by Dan_Dranath999 on 2009-05-19
Maybe the latest updates are the source of your stability issues. Fill a report, so new updates can fix it.

---

### Post by waspbr on 2009-05-19
try using metacity instead and see if that gives you more stability.

press Alt + F2 and type
```
metacity --replace
```

you can also enable composite effects, (not as flashy as compiz but still nice) by again pressing Alt + F2 and typing 

```
gconf-editor
```

There, go to apps>>metacity>>general and tick the compositing manager box

gl

---

### Post by mvalviar on 2009-05-22
It's conclusive Compiz IS causing hangs. Its been days since I turned off compiz and I haven't had a crash since then. 

How to do I report this so that developers can fix compiz?

For the mean time I'm using metacity. How do I get rid of the black box that appears everytime I minimize windows? It's kinda ugly and I'm wondering if its possible to remove it.

---

