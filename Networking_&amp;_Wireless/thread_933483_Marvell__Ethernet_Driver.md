---
title: "Marvell  Ethernet Driver"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by lapishc on 2008-09-29
I am new to Ubuntu...and running 7.10.  I am looking for a driver for a Marvell 88E8001 Gigabit Ethernet Controller (rev 13).

I grabbed this one...
[http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36](http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36)

Will this do it? How do I install it?

Thanks!!!

ccl

---

### Post by nixscripter on 2008-09-29
The link you posted goes to a search form. Could you try posting whatever file you actually downloaded?

---

### Post by bobnutfield on 2008-09-29
I believe that card uses the skge.ko module.  Open a terminal and type:

> sudo lsmod

look for a net driver with that name

---

### Post by lapishc on 2008-09-29
I believe the actual driver I donwnloaded is called sk98lin will that work for this ethernet card?

---

### Post by bobnutfield on 2008-09-29
I don't believe you needed to download it as it is already included in the kernel if you are running Hardy.  Type:

> sudo lsmod

and post the results.

---

