---
title: "Guarddog settings to allow CUPS printer sharing?"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-08-27
Kubuntu Edgy


Hi,

I have a CUPS printer shared over an internal wireless network(aka port 631). 

Prior to installing Guarddog firewall GUI, I was able to sent print jobs to the CUPS printer via my internal wireless network.

However, after installing Guarddog, I am not able to print. 

Does anyone know what protocols I would have to allow?



Thanks

---

### Post by DapperMe17 on 2007-08-29
Anyone?

---

### Post by kevdog on 2007-08-30
Can you confirm that is the port number???

Just add the port number as a custom port in the advanced tab, (new protocol under user defined protocols). Then go back to your protocol tab, and in the Zone Properities dialogue it should be listed under User defined -- you will need to add a check box to activate it!

---

### Post by DapperMe17 on 2007-09-01
Thanks Kevdog...will give that a try!

---

