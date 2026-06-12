---
title: "How to install network driver?"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by valmy on 2005-11-03
My ethernet card wasn't detected by the Breezy installation process. It suggested to manually configure the modules, but the installation process continued without networking.

Then I am able to setup the networking by:

```

sudo modprobe 3c509

```

And then setting up the rest of the configuration by the Network Administrator GUI. The network is up and running fine, but when I rebooted, I have to load the module manually again.

I try to add 
```

alias eth0 3c509

```
to /etc/modules, but that doesn't seem to be working. The module is still not loaded during boot and it doesn't even mentioned in /var/log/messages.

---

### Post by mlomker on 2005-11-03
I've never used *alias* in there before.  Did you try just listing 3c509 in /etc/modules?

---

### Post by valmy on 2005-11-05
OK, thanks, it works!

---

