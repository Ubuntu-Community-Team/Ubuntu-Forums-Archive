---
title: "pppoe configuration problem"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by nirakarsethy on 2008-05-20
Hi,
   I installed Ubuntu 8.04. I configured the pppoe with "pppoeconf"
The problem is how can I stop and start whenever I wish. 

Thanks

---

### Post by SpaceTeddy on 2008-05-20
two solutions:


1.)
start the connection with 
```
sudo pon dsl-provider
```

stop the connection with
```
sudo poff
```

2.)
or, as soon as you ran pppoeconf there will be a new button in network manager name dsl-prover which you can choose to dial into the internet

hope it helps :)

---

### Post by nirakarsethy on 2008-05-21
sudo pon service provider. Can you please give me a example. Suppose my service provider is "cable". So how should i do it ?

thanks

---

### Post by SpaceTeddy on 2008-05-21
pppoeconf is uses a standard name for the configuration, which is dsl-provider. No matter what your ISP is called, if it cable or not, as soon as you have configured your dialin via pppoeconf your provider will always be called dsl-provider.

and yes, it's sudo for executing the command as root - then pon (which is a wrapper script for ppp) to dial out and dsl-provider to tell it which configuration file to use.

that's pretty much all there is... i don't know of anything else :(

---

