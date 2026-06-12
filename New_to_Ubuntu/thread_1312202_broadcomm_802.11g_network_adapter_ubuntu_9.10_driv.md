---
title: "broadcomm 802.11g network adapter ubuntu 9.10 driver"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by agquintero on 2009-11-02
Does anyone know how or where I can find the drivers for that network card for my really old and beat up laptop. I installed the netbook version and the wireless card does not work. Please help!

---

### Post by NickJones on 2009-11-02
Can you give us any more info? There were a verity of Broadcom 802.11 cards made.

---

### Post by agquintero on 2009-11-03
Unfortunately I cannot find any extra information about the card. I'm currently running windows xp on my laptop because i cannot connect to the net wirelessly. And when i check my hardware specs it it just says it's a Broadcom 802.11g Network Adapter.... it's the one that came with my laptop. An acer aspire 3000 series... an oldie... lol. Thanks in advance.

---

### Post by agquintero on 2009-11-04
ok... i did a little more research and i found out this

   PCI\VEN_14E4&DEV_4318&SUBSYS_03121468&REV_02\3&267A616A&0&58
  
is that information any help to anyone that could help me?

---

### Post by KIAaze on 2009-11-05
Post the output of:
```
lspci -vvnn
```
;)

---

