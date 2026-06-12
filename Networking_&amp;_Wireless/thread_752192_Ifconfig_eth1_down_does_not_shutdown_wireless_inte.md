---
title: "Ifconfig eth1 down does not shutdown wireless interface"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by GutsyGibbonMarc on 2008-04-11
I have two wireless interfaces: an internal and an external one. I want to shutdown the internal wireless i/f temporarily.  I do not want to blacklist it. So I do an "ifconfig eth1 down" and I watch from another laptop that the interface is still probing. I wait some more but the interface never shuts down.   I do an "ifconfig" and the interface appears to be down. For grins,  I then turn an AP that the i/f has associated with before. A few minutes later, I do an "ifconfig" and the the OS reports the i/f is up.  The icon also shows it is associated. 

So it appears that ifconfig eth1 down does not work at all.  Is that a bug or a feature? What can I do? 

I am running Ubuntu 7.10.  The internal wifi is an Intel 2200BG.  It appears to be using the ipw2200 module/driver.

Thanks!

Marc

---

### Post by dstew on 2008-04-11
> I watch from another laptop that the interface is still probing. I wait some more but the interface never shuts down.What do you mean by this? The command ifconfig eth1 down does not turn off the card's transmitter, only disables the software interface with your system. To turn off the card, you would need to do something like```
iwconfig eth1 txpower off
```

---

### Post by GutsyGibbonMarc on 2008-04-11
> **dstew said:**
> What do you mean by this? The command ifconfig eth1 down does not turn off the card's transmitter, only disables the software interface with your system. To turn off the card, you would need to do something like```
iwconfig eth1 txpower off
```

Thank you for the reply and the command. I am running wireshark on the other machine. So I can see the 802.11 probe requests even after I shut down the i/f (e.g. ifconfig eth1 down).  What is interesting is that the association does not tear down either. And once I start Firefox, the interface will report that its status i now up. I will try the txpower switch and let you know if that works.

Marc

---

### Post by GutsyGibbonMarc on 2008-04-11
"iwconfig eth1 txpower off" does the trick.  Thanks!

---

