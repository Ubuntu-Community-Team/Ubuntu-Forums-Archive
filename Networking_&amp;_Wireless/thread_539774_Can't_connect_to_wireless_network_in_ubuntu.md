---
title: "Can't connect to wireless network in ubuntu"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by dowler on 2007-08-31
I just installed ubuntu and am new to it.  I have a Linksys WMP54G nic.  Ubuntu shows my network, which is not secured, but it wont connect to it.  What do I have to do to get this to work?  Will the RT61 driver fix this problem?

---

### Post by doublearon on 2007-08-31
Hey I'm also  a newb, but I *can* tell you that you'll probably need ndiswrapper. I would search the forum for your model card, ndiswrapper, etc. I'd also try google. I had the same exact symptom (not the same hardware though) before I read a howto for my card on a dell laptop. I won't send you to the howto because it doesn't apply to your card. 

If there's one thing I've learned so far, it's that Linux makes you READ. You read, then you read some more, then you keep reading. For me personally, it's worth it.

---

### Post by gundumfx on 2007-08-31
> **dowler said:**
> I just installed ubuntu and am new to it.  I have a Linksys WMP54G nic.  Ubuntu shows my network, which is not secured, but it wont connect to it.  What do I have to do to get this to work?  Will the RT61 driver fix this problem?

well what are you using a laptop right ??

---

### Post by dowler on 2007-08-31
> **gundumfx said:**
> well what are you using a laptop right ??

no, deskotop.  it seems to recognize my nic fine, it just doesn't want to connect.

---

### Post by doublearon on 2007-09-04
Have you tried to use ndiswrapper with a windows driver for it? It's going to take a little reading.

---

### Post by kevdog on 2007-09-04
Can you post

lspci -nn
lshw -C network

If your device really uses an ra based chipset, then I would opt for installation of rt serial monkey drivers over ndiswrapper.

---

