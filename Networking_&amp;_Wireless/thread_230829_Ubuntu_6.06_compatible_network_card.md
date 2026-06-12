---
title: "Ubuntu 6.06 compatible network card"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by cerpin_taxt on 2006-08-06
I've recently installed Ubuntu on my machine (WinXP/Ubuntu dual boot), and have noticed that I cannot get it to connect to my network with the built-in ethernet plug on my computer.  Can anyone:

A) Tell me how to get an internet connection with the hardware I already have in my computer.

B) Recommend me a network card that will allow me to connect to my network.

I'm not sure if it matters, but I'm using a DLink DI-524 router connected to the main computer in my house and a cat5 cable stretched between it and my computer to access the internet.

I'd also prefer that the card not be PCI-E, as I'm saving that slot for the graphics card I plan on buying.  :\

---

### Post by sir_mud on 2006-08-06
Can you post your results from lspci?

---

### Post by cerpin_taxt on 2006-08-06
Just open the terminal and type lspci?  Or is there more to it than that?

---

### Post by sir_mud on 2006-08-06
Also, try running network-admin, System->Administration->Networking, make sure your ethernet device is configured and active...if it even shows up.

---

### Post by sir_mud on 2006-08-06
That's all you have to do, it should say Ethernet controller or such.

---

### Post by cerpin_taxt on 2006-08-06
In Sys>Admin>Networking, it shows my modem (which I don't use), and eth0.  I have it set to a dynamic IP address.  Is there a way to tell if its configured and active?  I've not been on the ubuntu side of my computer in a while, so I'm not sure exactly what it said.  Let me download FS-Drive so i can access the lspci results after I save them.

---

### Post by sir_mud on 2006-08-06
Under Eth0 it should say "this interface is active" ,
if not, highlight it then click activate.

---

