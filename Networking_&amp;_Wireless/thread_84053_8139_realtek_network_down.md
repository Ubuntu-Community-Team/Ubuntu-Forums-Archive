---
title: "8139 realtek network down"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by josir on 2005-10-30
Hi folks,

I can´t access the network with a realtek card.

UBUNTU recognizes the module on Device Manager but when I try:

ifconfig eth0 up

I got error: "SIOCSIFFLAGS: Função não implementada"

Somebody has any tip or suggestion?
Thanks in advace,
Josir Gomes

---

### Post by jmcnaught on 2005-11-01
Hi,

I don't read portugese, but I'm guessing that says "function not implemented."

You may have already tried this, but since it's not mentioned in your post: have you run the same command with sudo?  If I run ifconfig eth0 up without sudo, I get the error "SIOCSIFFLAGS: Permission denied" so I'm guessing you're root.  For anybody else reading this topic:

sudo ifconfig eth0 up

good luck

Jeremy McNaughton

---

### Post by josir on 2005-11-02
Hi Jeremy,
thanks for replying. Your translation was perfect. 

I think that this a hardware problem because Mandrake and Win2000 didn't installed correctly either.

Josir

---

