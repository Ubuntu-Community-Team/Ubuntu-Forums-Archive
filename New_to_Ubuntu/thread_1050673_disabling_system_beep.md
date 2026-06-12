---
title: "disabling system beep?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2009-01-25
everytime my computer does a system beep the following graphical errors happens and my screen starts flashing the following image below for like 10 seconds
probably the freakiest thing thats every happened to me computer related

---

### Post by utnubuuser on 2009-01-26
Nvidea card?  Ubuntu 8.10?

---

### Post by x33a on 2009-01-26
add this line :

blacklist pcspkr

to /etc/modprobe.d/blacklist

---

### Post by SpenceMakesSense on 2009-01-26
> **utnubuuser said:**
> Nvidea card?  Ubuntu 8.10?

yep. This only happens when I have a second x server setup on my tv. But instead of disabling the second server I just wanted to get rid of what causes it.

---

### Post by HavocXphere on 2009-01-27
> **x33a said:**
> add this line :

blacklist pcspkr

to /etc/modprobe.d/blacklist
Works like a charm. Thank you.\\:D/

---

### Post by SpenceMakesSense on 2009-01-29
Disabled system beep but still have the graphical error. So whatever is telling the computer the to system beep despite having one or not is causing my computer to have that graphical error. 

If I disable compiz it doesnt happen. This only happens when I have my second x server setup and compiz enabled.

---

### Post by SpenceMakesSense on 2009-01-30
bump

---

