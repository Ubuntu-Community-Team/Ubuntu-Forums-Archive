---
title: "[SOLVED] Wireless LAN not available on Dell Vostro 1000"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by meetu on 2007-08-24
I have been trying to setup my wireless network working on my brand new Dell Vostro 1000 with AMD Turion 64 x2 processor. The Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card seems to be unsupported by Ubuntu. I tried using ndiswrapper but till now it hasn't worked.

---

### Post by moore.bryan on 2007-08-24
[I]what are the outputs of ```
iwconfig
lspci
```?
[/I]

---

### Post by meetu on 2007-08-27
Now the problem is resolved, the problem reappeared when I upgraded version to feisty fawn, it initially worked with ndiswrapper. When I tried that on feisty fawn I was not able to bring my WLAN at all. I redid the steps and now things are working fine.

---

### Post by moore.bryan on 2007-08-27
[I]glad you got it figured-out!  you should use the "thread tools" link at the top right and mark this solved.
[/I]

---

### Post by meetu on 2007-08-28
Thanks Bryan.

---

### Post by moore.bryan on 2007-08-28
*no problem... happy ubuntu-ing.*

---

### Post by Spam Banjo on 2007-08-28
> **meetu said:**
> Now the problem is resolved, the problem reappeared when I upgraded version to feisty fawn, it initially worked with ndiswrapper. When I tried that on feisty fawn I was not able to bring my WLAN at all. I redid the steps and now things are working fine.

I got the Vostro 1000 with the 1390 Mini PCI and am really pulling my hair out. I've been using Ubuntu for a few months and have had some teething trouble! Got most things going but the wireless has evaded me every time, on every machine!

Any chance you could point me in the right direction??

I followed a few guides but got nothing. This is killing me!

---

