---
title: "Edgy - Cannot access network"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by adam_lipscombe on 2007-03-22
I am complete newbie to Ubuntu so forgive me of this is a no brainer:

I recently installed Edgy and it worked well.
I had a power cut 3 days ago, and on rebooting the machine can no longer access the network.

The machine is connected by ethernet to a ADSL modem/router, and is configured to use DHCP.
The green light is on the the back of the network card is lit and the cables are secure.


I have tried altering to a static IP address using the network admin tool and then back to DHCP but it makes no difference.

I have 2 other windows machines on the network and they work fine, so the problem cannot lie with the router.


I suspect the sudden power down has messed something up but I have no idea where to start looking.


Can anyone help?


TIA - Adam

---

### Post by bloodniece on 2007-03-22
Adam,

Please run these commands and post the results back here.

Copy and paste them into the terminal window 
* To paste into a terminal press: ctrl+shift+V*

[B]Applications --> Accessories --> Terminal

[/B] ```
ifconfig
```*We are not running this as root, we're just looking at the contents of the file. We are not changing it, yet.*
```
gedit /etc/network/interfaces 

```

---

### Post by adam_lipscombe on 2007-03-23
Many thanks


The damn thing has started to work again today.
I have no idea why :-(

---

