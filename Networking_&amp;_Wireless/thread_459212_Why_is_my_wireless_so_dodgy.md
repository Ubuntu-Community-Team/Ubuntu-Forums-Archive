---
title: "Why is my wireless so dodgy?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by ret3 on 2007-05-30
On about 1 in 5 reboots, I get a few minutes of wireless connectivity via my HP-branded Lucent Orinoco Wireless PC Card. 

In a previous thread, chili555 suggested I post the out put of lsmod | grep orinoco, lsmod | grep hostap, and lsmod | grep prism2.

Only lsmod | grep orinoco returned anything: 

orinoco_cs 16900 1 
orinoco 43028 1 orinoco_cs
hermes 8448 2 orinoco_cs,orinoco
pcmcia 39212 1 orinoco_cs
pcmcia_core 40852 4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

What now?

---

### Post by benmoreassynt on 2007-05-30
i have different hardware, but I have found that the default Ubuntu setup would drop my connection all the time. Instead I shifted (back) to using ndiswrapper for wireless. It is much more reliable, and never drops the connection for me. Not sure if that will be any help.

---

### Post by ret3 on 2007-05-30
Ndiswrapper shouldn't be needed for this card; the orinoco chipsets are supposed to be directly compatible. I might give that a shot if I don't get any other help!

---

