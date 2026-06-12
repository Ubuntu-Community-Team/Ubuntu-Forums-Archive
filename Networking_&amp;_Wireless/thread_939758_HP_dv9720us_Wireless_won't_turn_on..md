---
title: "HP dv9720us: Wireless won't turn on."
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by irmcewen on 2008-10-06
Hello.

I have an HP dv9720us that I just installed 64-bit Hardy Heron on. Everything is working splendidly with one issue; I can't get the wireless adapter to turn on for the life of me.

The laptop has a switch on the front of it and when it's pushed to the right and wireless is on the light normally turns blue. No matter which position the switch is in now the light remains orange and the wireless adapter remains off. The laptop has an Atheros wireless adapter built in and from what I can tell the driver is installed properly, but I just can't get it to turn on.

Has anyone experienced a similar problem and could someone perhaps provide some insight into how to fix the problem? Thanks so much for any help you can give me.

Cheers,
IRM

---

### Post by Bucky Ball on 2008-10-06
> **irmcewen said:**
> Hello.

I have an HP dv9720us that I just installed 64-bit Hardy Heron on. Everything is working splendidly with one issue; I can't get the wireless adapter to turn on for the life of me.

The laptop has a switch on the front of it and when it's pushed to the right and wireless is on the light normally turns blue. No matter which position the switch is in now the light remains orange and the wireless adapter remains off. The laptop has an Atheros wireless adapter built in and from what I can tell the driver is installed properly, but I just can't get it to turn on.

Has anyone experienced a similar problem and could someone perhaps provide some insight into how to fix the problem? Thanks so much for any help you can give me.

Cheers,
IRM

Common problem. Try having a look on the net using:

Atheros Ubuntu

... and you will find plenty.

Could you open a terminal and paste this in (Applications->Accessories->Terminal):

**lspci**

Then paste the results in your next post please. That will identify your card.

* Update: Try this page ...

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

.. go from 'Prepare Your System' after the part about i386 systems. Add the instructions to your terminal one by one, not all at the same time.

---

### Post by irmcewen on 2008-10-06
> **Bucky Ball said:**
> 
* Update: Try this page ...

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

.. go from 'Prepare Your System' after the part about i386 systems. Add the instructions to your terminal one by one, not all at the same time.

Thanks so much for the speedy reply. I will try this when I get home from work this afternoon.

> **Bucky Ball said:**
> 
Could you open a terminal and paste this in (Applications->Accessories->Terminal):

**lspci**

Then paste the results in your next post please. That will identify your card.

If the above method you posted about does not work I will post the results of this command later today. Thanks so much once again.

Cheers,
IRM

---

