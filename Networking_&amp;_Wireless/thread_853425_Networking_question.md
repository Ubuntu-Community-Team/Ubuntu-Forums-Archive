---
title: "Networking question"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by hman469 on 2008-07-08
I am running Ubuntu 8.04 and I want to know is it possible to use a Linksys WUSB54GS ver.2 for my internet connection while using my ethernet card wired to a hub to access other computers (1 running Windows, 1 running Open Suse, and 1 running Xubuntu) and sharing the internet connection from the wireless to the computers on the wired hub?

If this is possible could someone point me in the direction of a tutorial to do it please?

Thanks

---

### Post by Paul Weaver on 2008-07-08
Yes it is
First you need to get the wireless working, this will probably be the "eth1" interface
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

Then you need to use ip tables and nat, your external interface is the wireless card, the internal interface is the cable card.
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

P.S. If you use a more specific title ("sharing internet with a wusb54g" or something) your thread is more likely to get noticed by the right person!

---

### Post by The Minder on 2008-07-08
I'd suggest you find an old computer (and it really doesn't need to be a powerful box) and install IpCop on it.   IpCop will provide the internet access you're looking for across the network, do DHCP, and provide terrific security.   IpCop is free, it works, and no I'm not affiliated with the product.

Regards

---

### Post by hman469 on 2008-07-09
> **Paul Weaver said:**
> Yes it is
First you need to get the wireless working, this will probably be the "eth1" interface
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

Then you need to use ip tables and nat, your external interface is the wireless card, the internal interface is the cable card.
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

P.S. If you use a more specific title ("sharing internet with a wusb54g" or something) your thread is more likely to get noticed by the right person!

I greatly appreciate the quick reply but being a total noob at linux I am wondering if this is something I am ready to attempt. I definitely want and need my machine set up this way just not sure if I am ready to risk messing up my system.

---

### Post by hman469 on 2008-07-09
> **The Minder said:**
> I'd suggest you find an old computer (and it really doesn't need to be a powerful box) and install IpCop on it.   IpCop will provide the internet access you're looking for across the network, do DHCP, and provide terrific security.   IpCop is free, it works, and no I'm not affiliated with the product.

Regards

I only have one machine that can decrypt the packets or whatever the wireless unit receives without constantly shutting down and/or locking up. Thanks for the reply though.

---

