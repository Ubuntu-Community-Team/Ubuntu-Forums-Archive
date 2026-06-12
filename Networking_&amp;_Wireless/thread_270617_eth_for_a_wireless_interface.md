---
title: "eth for a wireless interface??"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by on~namas~ganga on 2006-10-03
Hello 

Anybody could explain why Ubuntu Dapper 6.06 has recognised my wireless card, has load the modules and drivers aparently perfectly, but it is calling the wireless interface as eth1, it should be wlan1 instead... how can I change it? it might be why I still can´t connect although I see open networks around me. 
I have an ibm g40 with Wireless card MicroPCI III ( chipset Intersil Prism 2.5 and seems that hostapd driver is taking care of it...
Anyway, first of all, why to put a eth and not wlan...?

Thanks in advance :-k

---

### Post by louis_nichols on 2006-10-03
It's just the default way that the kernel names network interfaces. It's a convention, as there aren't any standards for that.You can certainly change this, but I'm afraid it won't be easy. You might need to tweak the kernel sources and then compile your own kernel. Highly not recommended unless you are a programming guru.

In the end, it's not such a big deal, right? As long as you know what the interface is.

---

