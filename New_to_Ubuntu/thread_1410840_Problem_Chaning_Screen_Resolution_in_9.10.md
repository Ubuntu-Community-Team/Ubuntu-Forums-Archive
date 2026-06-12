---
title: "Problem Chaning Screen Resolution in 9.10"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by sudeepk on 2010-02-19
I am using ubuntu 9.10. I am trying to change screen resolution through System>Preference>Display. But i have only two options given 800x600 and 640x480. I don't any graphic card. How can i change the screen resolution to 1024x786?

---

### Post by Julita on 2010-02-19
lspci, please.

---

### Post by sudeepk on 2010-02-19
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by Julita on 2010-02-19
OK, this card has its resolution issues. Sometimes this would help: 
in terminal, type sudo /etc/init.d/gdm stop (you will be dropped to a non-graphical environment), then
sudo X -configure (follow the instructions)

---

### Post by sudeepk on 2010-02-19
I tried doing the above. I have stopped gdm and i have run the commmand x-configure. But the command isn't available. I tried to install it but the synaptic says there is no package called x-configure. what to do now?

---

### Post by Julita on 2010-02-19
You had to run the command just as I have typed. Did you do that? Try once more please 
sudo /etc/init.d/gdm stop
sudo X -configure (not x-configure; preserve the upper case for X)

---

