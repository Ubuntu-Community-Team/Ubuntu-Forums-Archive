---
title: "No bootable device"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-11-23
My computer has been having issues lately the most annoying occurs at boot up. When I first turn on my little Acer One loaded only with Ubunto 10.04 I get the following :

Intel UNDI, PXE-2.1 (build 002)
Copyright (C) 1997-2000 Intel corporation

For Atheros PCIE Ethernet Controller v1.0.0.5(01/22/09)

Check cable connection..!
PXE-E63: error while initializing the NIC
PXE-MOF: Exiting Intel PXE ROM
No bootable device--insert boot disk and press any key.

I then cntl-alt-del and on reboot it finds its boot drive and the loads the OS
 I F2 on start up and checked to ensure that my HD was listed first during boot up possess. It appears as such:

1. Network Boot: Atheros Boot Agent
2. IDEO: ST9160314AS
3. IDEI:
4.USB FDD
5.USB HDD
6.USB CDROM

I then F10 and again it will boot fine. 

Problem is I have to do this EVERY time I turn the unit on. I have to either cntl-alt-del after it first attempts boot up OR I will hit F2 during iniital boot up tab over to Boot Tab strike F10 then enter and again all is fine. How do I correct this

---

### Post by yankysunny on 2010-11-23
I think it check you network device everytime for the bootable device. Pu t your HD on top of the list and see what happens

---

