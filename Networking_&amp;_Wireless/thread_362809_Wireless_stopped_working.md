---
title: "Wireless stopped working"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by ASpott on 2007-02-16
I have an ibm x60 with ubuntu edgy eft 6.10 on it. For a couple months the wireless has been running fine on it up until recently. I don't know if its just a coincidence but I installed the latest group of updates that prompted me to reboot my computer and when I rebooted my wireless card was no longer working. When I run iwconfig I get:

lo         no wireless extensions.

irda0    no wireless extensions. 

sit0       no wireless extensions. 

eth0     no wireless extensions. 

The network settings manager no longer shows a wireless card either. I don't really know what I'm doing or really even where to start so if anyone has any ideas on why my computer would forget I have a wireless card that would be awesome. Or just a link to a document that might help. Thanks.

---

### Post by gradedcheese on 2007-02-16
> 
I don't know if its just a coincidence but I installed the latest group of updates that prompted me to reboot my computer and when I rebooted my wireless card was no longer working.

Yes, that's actually the cause.  Reboot and press ESC for the grub menu, and then select the second-to-newest kernel (ie: your previous kernel).  Boot up and confirm that the WiFi now works.

---

### Post by sdide on 2007-02-16
Hey,

Can you post your output of  /etc/network/interfaces

```
#  cat /etc/network/interfaces
```

---

### Post by ASpott on 2007-02-16
Thanks, you're right, it does work with a previous kernel. But now that I know that its a problem with the kernel, how do I go about fixing that?

---

### Post by futz on 2007-02-16
> For a couple months the wireless has been running fine on it up until recently. I don't know if its just a coincidence but I installed the latest group of updates that prompted me to reboot my computer and when I rebooted my wireless card was no longer working
I just noticed that my wireless has quit working too since the "upgrade" to the new kernel. I rarely use wireless, so didn't notice it till tonight. If I reboot to the older 2.6.17-10-386-generic it works again.

That's kind of annoying.

---

