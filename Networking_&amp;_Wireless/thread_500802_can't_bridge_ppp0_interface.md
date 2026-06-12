---
title: "can't bridge ppp0 interface"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by A-1337 on 2007-07-14
Hello!
I have ubuntu feisty workstation. I access internet through ppp0 interface. Also I access bluetooth-enabled PDA via PAN through bnep0 interface.
I want to share internet connection with PDA. Is it possible to do so bridging these interfaces with brctl?
bnep0 can be added to bridge but on adding ppp0 I get error:
```

can't add ppp0 to bridge pan0. Invalid argument

```

---

### Post by BDTM on 2008-07-15
Hello, first post!!

right, i am having the same problems and after much looking i found the MTU had to be changed.  I did this but it still didn't work even though other people had some success.

You need to run 

sudo ifconfig eth0 mtu 1440 

and this should set the MTU to the same as the PPP0.  (check the PPP0 MTU by typing ifconfig -a) 

However, like i said this still did not allow me to bridge the ppp0.  Any other ideas PLEASE????

Thanks in advance......

---

