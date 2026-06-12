---
title: "lost wireless interface with kernel update"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by oncemore on 2006-08-20
i think the title explains everything...
i had wireless support in kernel 2.6.15-23-386, and lost it when upgraded to kernel 2.6.15-23-686.
my wireless card is Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
i think that the new kernel doesnt have the drivers for this card but i dont know how to fix it.

---

### Post by Faytz on 2006-08-20
> **oncemore said:**
> i think the title explains everything...
i had wireless support in kernel 2.6.15-23-386, and lost it when upgraded to kernel 2.6.15-23-686.
my wireless card is Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
i think that the new kernel doesnt have the drivers for this card but i dont know how to fix it.

Same thing here

---

### Post by tombs on 2006-08-21
The drivers were not compiled for the new kernel.
You just have to re-compil it agian, following the same steps you did before, but with new kernel. Don't forget the kernel-headers.

---

### Post by oncemore on 2006-08-21
what steps?
the card was working fine with a fresh install of dapper.
do u know any howto?

---

### Post by lupine_nickt on 2006-08-21
You need to update your linux-restricted-modules package as well. 

If that doesn't work, then check out [http://madwifi.org/](http://madwifi.org/) for details of the driver, how to compile it yourself, etc.

xF,

...Nick

---

### Post by tturrisi on 2006-08-21
The drivers you need are included in the linux-restricted-modules for the new kernel.  Use synaptic to get 'em.

---

### Post by tombs on 2006-08-22
Howto.....try following this one please:

[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=atheros]("http://www.ubuntuforums.org/showthread.php?t=38972&highlight=atheros")

And tell us about the results :)

---

### Post by oncemore on 2006-08-22
I feel kinda stupid...just enabled the restricted repos and dwled restricted-modules and now it works...
but isntalling madwifi drivers from sources works as good ;)

---

