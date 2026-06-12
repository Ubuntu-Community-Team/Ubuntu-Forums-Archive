---
title: "PCMCIA slot not working in jaunty"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mbzn on 2009-05-17
Hi there,

My pcmcia slot stoped working after Jaunty upgrade.
I'm using a Dell Latitude d600 laptop and the slot was working with ibex but now when i stick my orinoco card in the lights dont even come on.

If anyone has an idea of where to start looking, Please share...

Thanx in advance

---

### Post by Aaardwark on 2009-05-17
```
dmesg | grep orinocco
or
dmesg | grep wifi

iwconfig

lsmod | grep orinocco
```

One of them should signal something if you pluged in card is noticed by the system.

---

### Post by mbzn on 2009-05-17
only response i get is from iw config and it only shows my internal wireless. how can i test my pcmcia slot?

---

### Post by Aaardwark on 2009-05-17
Well...then we know it doesn't find the card. Then we have the question of whether we can find the pcmcia at all.
```
dmesg | grep pci
dmesg | grep pcmcia
lshw
lspcmcia
```
Do you find anything of relevance?

---

### Post by mbzn on 2009-05-18
I think this is the problem

```

martin@mbzn:~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.1)
Socket 1 Device 0:	[-- no driver --]	(bus ID: 1.0)

```

now, why is my orinoco driver not installed & where do i get it?

---

### Post by Aaardwark on 2009-05-21
I've been busy a few days, surprised nobody has helped you yet. Seems your system has found the hardware, but no driver is installed. What specific wifi card and chip do you have?

---

