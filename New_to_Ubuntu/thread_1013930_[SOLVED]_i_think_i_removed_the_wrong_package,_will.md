---
title: "[SOLVED] i think i removed the wrong package, will not show desktop"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by unxzst on 2008-12-17
so i was removing packages i was not using with synaptic, now my desktop will not show. 
all i see is a beige background, and thats it. 
i cannot do anything except power down with the power button. 
i tried apt-get update in recovery mode, but i don't think the network card works like that. 
all i have now is a liveCD and this windows i'm using. 
please help!

---

### Post by taurus on 2008-12-17
I suppose you don't remember what programs/apps that you removed.  While at the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Hopefully it will reinstall whatever you have removed.

---

### Post by unxzst on 2008-12-17
i have no GUI login screen, i was able to get to the prompt from recovery mode.
networking will not load, apt-get says it cannot reach address

---

### Post by cariboo on 2008-12-17
To access the internet in recovery mode, at the prompt type:

```
dhclient eth0
```

This should get you an ip address and you should be able to restore your system back to working order.

Jim

---

### Post by unxzst on 2008-12-17
> **cariboo907 said:**
> To access the internet in recovery mode, at the prompt type:

```
dhclient eth0
```

This should get you an ip address and you should be able to restore your system back to working order.

Jim
thanks, Jim
```
dhclient
```
did it, eth0 parameter did not work.

no more experimentation for me. 

I was trying to optimize this for a friend. 
Ubuntu on a USB1 2Gb flash drive is still out of reach.

---

