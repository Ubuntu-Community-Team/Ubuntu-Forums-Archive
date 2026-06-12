---
title: "NIC issue on VMWare ubuntu image on many PCs"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Lycaone on 2010-11-25
Hi gurus,
I created my first vmware ubuntu image today on a USB key. I used it on my office PC and everythings was great (well I can surf web but I cant update but it is because of my automatic proxy script)
When I tried to use same image on my laptop I see that there is no network connection. I suppose this is because PC and notebook have different NICs. There is a way to force ubuntu to recognise NIC and so keep using it on different PCs?

Gianluca

---

### Post by cariboo on 2010-11-26
Virtualbox uses a virtual NIC, try setting it as a bridged adapter.

---

