---
title: "Can't get online through built in wireless laptop"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by guthrie.mark on 2008-07-07
Okay I've successfully installed Ubuntu on my laptop. Which currently is now duel boot with windows vista. My problem that I am having is that I'm having some difficulties trying to go online through a wireless server at a public library. It works when I'm using windows. But does not work with Ubuntu. Basically what I'm trying to do is install the codecs, so that I'm able to listen to mp3s and watch some dvds with Ubuntu and use windows as less as possible. Thanks for your help.

Mark.

---

### Post by comandrei on 2008-07-07
Can you tell us anything about your wireless card (manufacturer, firmware version stuff like that). We can't help you if we don't know your hardware configuration.

---

### Post by chalewa on 2008-07-07
hi do you know what kinda wireless card you have?

if not, post 

```
lspci
```

---

### Post by blazercist on 2008-07-07
in order to diagnose the problem you need to provide the output of these commands in terminal

```

sudo ifconfig

```

```

lsmod

```

depending on whether the wireless adapter in PCI or USB either:

```

lspci

```
or

```

lsusb

```
Also, you need to give us information about the security scheme in place on this network... is it WEP WPA etc...

---

### Post by guthrie.mark on 2008-07-07
For the network card It's built into the machine it self. So I'm not directly using a card. Basically what I do is right click on my network icon on my taskar and click what wireless network is available to me.

And as for the security theme of the network, there is no password to log in with. It's a public wifi. But I am pretty sure it's WEP.

---

### Post by chalewa on 2008-07-07
ok so in ubuntu, when you click on the network icon in the upper right hand corner (looks like two computers on top of each other sorta), do you see the wireless network in there or not?

can you still post what the output of 

```
lspci
```
and
```
lsusb
```
and
```
ifconfig
```

---

### Post by guthrie.mark on 2008-07-07
Okay I'm going to give that a try. I'm pretty sure it's something so simple, that I can't figure it out. LOL.

---

