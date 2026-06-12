---
title: "Using ZyAir G 200 wireless USB 2.0 adapter with Ubuntu"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by vivekrawal on 2005-12-03
HELP!!!!!

I am using  ZyAir G 200 wireless adapter (external) for my desktop. I have just installed Ubuntu on my system. But unable to access internet through ubuntu. It seems the adapter has not been recognised by the breezy on its own during installation. I am new to linux. Have already installed ubuntu on my laptop and i am very happy with its performance there. But do not know how to configure internet access on my desktop. Could any one guide me step by step how to enable my internet access?
thanks in advance.

Vivek

---

### Post by cracker on 2005-12-03
You probably need ndiswrapper. Try the instructions here:

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

---

### Post by vivekrawal on 2005-12-04
I installed ndiswrapper from ubuntu CD using synaptic. After that i have also installed  windows driver from Zyxel CD using ndiswrapper. I realise that it was not the best way of installing the driver and should have gone to the website for download but i do not have the net access on that machine. 

after installation i used following command 
ndiswrapper -l
 it shows me installed drivers
win502u driver present, hardware present

after this, I used command
sudo modprobe ndiswrapper


after this I tried to configure networking in system>administration>networing 
but I can not see wlan0. I see only ethernet (eth0) and modem and both are not activated. 

CAN I GET HELP ON HOW TO GET NDISWRAPPER WORK FOR ME?

i have AMD athlon 2400 processor

Thanks

Vivek
[QUOTE=cracker]You probably need ndiswrapper. Try the instructions here:

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)[/QUOTE]

---

