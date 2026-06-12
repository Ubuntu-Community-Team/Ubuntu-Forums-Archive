---
title: "need info for wired internet (ethernet) connection"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by edthetermite on 2009-02-09
looking for wired network directions to set up new install.
I have a dual boot os that has XP up and running and successfully connects to the internet through a wired LAN connection. Ubuntu is not seeing the settings and I need info to properly configure. 
I am using a P5N73-AM Asus motherboard with built in LAN connection. Chipset drivers are installed as this mobo uses "Phyceiver" [Realtek RTL 8201CP] device technology. 

Thanks,

Ed

---

### Post by Shazaam on 2009-02-10
You might need drivers not supplied by a default Ubuntu installation. Go to System>Administration>Hardware Drivers and see if there are any drivers you can activate (install). If there are no choices there do this--
Open terminal (Applications>Accessories>Terminal), type this in and post back with the result...
```
lspci
```
This code will print out your hardware info.

---

