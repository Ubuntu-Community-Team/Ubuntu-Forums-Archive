---
title: "Getting a com port to work with virtualbox/xp"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-06-15
I am having a nightmare time getting my com port to work with virual box.

I am trying to get the 9 pin mouse port to work with a AVR programmer. I have tried just putting in com1..4, windows detects but no dice. I think I need to set a host device and have tried /dev/tty0 but virualbox doesnt like that and refuses to boot up, says it cant find the port ( i think )

Any suggestions?

---

### Post by niteshifter on 2009-06-15
Hi,

Try mapping it to /dev/tty**S**0 or /dev/tty**S**1 in the host. /dev/ttySN, where N = 0 to 3 for the 'classic' COM1 to COM4 devices.

---

### Post by Mick8882003 on 2009-06-15
I have tried mapping it to /dev/ttyS0 to 9 didnt help any.

At the moment I have it mapped from com1 to s0 using host device is that how it should be?

---

### Post by Mick8882003 on 2009-06-15
Bump

---

### Post by Mick8882003 on 2009-06-16
Bump

---

