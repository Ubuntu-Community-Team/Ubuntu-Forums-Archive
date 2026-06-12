---
title: "ethernet connection"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-17
I have my Toshiba connected via WAN to the internet..  Can I tether another mini PC to it via an Ethernet cable and connect the mini that way..???? I need to download some stuff to the mini before it can connect on its own..

---

### Post by albert s on 2010-03-17
AFAIK you will need a null cable,
ie, one with a crossover, you can also buy adapters for standard cables,
or make your own if you have the jacks and a crimp tool , I can let you know the pin/colour configurations

---

### Post by Iowan on 2010-03-17
If you happen to have a hub, switch, or router, you can use straight cables. Were you intending to share files between the two machines - or are you trying to set up Internet/Connection sharing?

---

### Post by 3948ctyj on 2010-03-17
I have the 5 port Linksys switch...  I tried linking everything together but it didnt work..??? The Toshiba just tried to establish a wired connection and it couldnt...

---

### Post by achase79 on 2010-03-17
you need to bridge the connection using the package bridge-utils.
it is in synaptic

---

### Post by 3rdalbum on 2010-03-18
> **achase79 said:**
> you need to bridge the connection using the package bridge-utils.
it is in synaptic

You don't need that, actually. The second connection (the one that the other computer will be connected to) can be added in Network Manager and under the IPv4 Settings tab you choose "Shared to Other Computers".

---

### Post by 3948ctyj on 2010-03-18
I did that and it didnt work. I was surprised. I tried one with that setting and then both with that setting..  
no go.
  I got the mini connected anyway to internet ,other means, but would still like to be able to connect others in the future.

---

