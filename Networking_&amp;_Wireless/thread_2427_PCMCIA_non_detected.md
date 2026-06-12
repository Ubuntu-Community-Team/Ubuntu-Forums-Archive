---
title: "PCMCIA non detected"
date: 2004-10-28
forum: Networking &amp; Wireless
---

### Post by indre on 2004-10-28
Hi!
Sorry for my english :-)
i have installed ubuntu.
then i have updated the kernel to version 2.6.9

now my pcmcia card is not detected...
i can't use kernel 2.6.8 because i have deleted file .config

so what kind of problem can it be?
have i forgotten some modules in kernel?
my pcmcia is level one 10/100 mbps

thanks a lot

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=indre]Hi!
Sorry for my english :-)
i have installed ubuntu.
then i have updated the kernel to version 2.6.9

now my pcmcia card is not detected...
i can't use kernel 2.6.8 because i have deleted file .config

so what kind of problem can it be?
have i forgotten some modules in kernel?
my pcmcia is level one 10/100 mbps

thanks a lot[/QUOTE]


Which .config did you delete?  The kernel-source .config.  You could also use
```

make oldconfig

```

Or try reinstalling the kernel src for Ubuntu's stock kernel.  Then your .config will be replaced by the default.  There are many ways around it.  

You may have forgotten a few PCMCIA modules. 

```

lspci

```

To see if the card is detected.

---

