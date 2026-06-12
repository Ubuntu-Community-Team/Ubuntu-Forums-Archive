---
title: "Wireless Problem"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by over2seeu on 2008-05-22
I am trying to get my wireless to start working.
I am running Xbuntu on my laptop.
I have installed Ndiswrapper and it still isn't working.

---

### Post by Ayuthia on 2008-05-22
Can you post your lspci -nn (from the Terminal)?  It will help us figure out what wireless card you have.  Thanks!

---

### Post by over2seeu on 2008-05-22
I don't know what I have.
How do I find it?

---

### Post by Ayuthia on 2008-05-22
> **over2seeu said:**
> I don't know what I have.
How do I find it?

Unfortunately, there is no GUI version that provides this information.  I think that Xubuntu might use Xterm.  If you can find this, can you go into it and type:
```
lspci -nn
```

---

### Post by over2seeu on 2008-05-22
I put that code in Terminal and got:

Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

---

### Post by Ayuthia on 2008-05-22
> **over2seeu said:**
> I put that code in Terminal and got:

Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

I think that is your wired card.  Is there another one that has Network Controller or Ethernet Controller?

---

### Post by over2seeu on 2008-05-22
there is: 
Ethernet controller (which I gave you)
FireWire
and SD host

---

