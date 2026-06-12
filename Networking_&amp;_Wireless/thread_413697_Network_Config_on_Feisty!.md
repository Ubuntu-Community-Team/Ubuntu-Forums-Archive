---
title: "Network Config on Feisty!"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by hdotcom on 2007-04-19
Hi all,

A fresh new installation (+updates) of feisty still doesnt recognize my ethernet card. I have ThinkPad T60. Please have a look at the output below. 

lshw -C network
```

 *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f 

```

ifconfig only displays auth0, lo and wifi0. One other thing to mention during the boot under "Configuring Network Cards" it mention and error trying to cat to ACPI-Support!

 Am really stuck here, i'd really appreciate it if someone can help me out here !:(

---

### Post by chili555 on 2007-04-19
I believe```
sudo modprobe e1000
``` will coax your ethernet adapter out of hiding.

---

### Post by hdotcom on 2007-04-20
Hi..

Unfortunately the network card is still hiding! :(  Any other ideas?!?! I really don't want to switch back to 6.10 or install SuSe!. Can anyone please help?!!?!?!

Thanx,

H.

---

### Post by GTvulse on 2007-04-20
> **hdotcom said:**
> Hi..

Unfortunately the network card is still hiding! :(  Any other ideas?!?! I really don't want to switch back to 6.10 or install SuSe!. Can anyone please help?!!?!?!

Thanx,

H.

After you do the modprobe, you have to check if the card is recognized by the system. In the same terminal window where you did the modprobe type "[FONT=Courier 10 Pitch]dmesg | tail -20[/FONT]" immediately after. You should see if the hardware was activated.

If the network interface was recognized by the driver you will need to configure it. The easy way is to use the graphical configuratior. Either do a left-click on network-manager icon on the top-right and select manual configuration or select "System->Administration->Network" to bring up the network settings applet. The network interface should applear there and you will be able to configure it (use DHCP if you can, it is the no-brainer option). Then take the connection down and up again either with the network-manager or clicking the check box in the network settings applet. KDE and XFCE use diferent applications but the procedure is the same.

---

### Post by hdotcom on 2007-04-20
Hi there..

Unfortunately eth0 is still not detected and was not showing on network-manager. I did another experiment and i installed OpenSuSe 10.2.....and guess what ...it was still hiding. Am sure it works ...at least under windows xp and ubuntu 6.10. Could this be a kernel issue ? If so how can i get it fixed?

Rgds,

H.

---

### Post by chili555 on 2007-04-20
Does this help? [http://ubuntuforums.org/showthread.php?t=409281](http://ubuntuforums.org/showthread.php?t=409281)

---

### Post by hdotcom on 2007-04-20
Nope it doesnt unfortunately!! Whats pissing me off is that the output from the dmesg command shows that it has detected the son of a gun!! Dont really know what else to do!

```

[    3.320000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    3.320000] Copyright (c) 1999-2006 Intel Corporation.
```

---

### Post by hdotcom on 2007-04-20
Alriggggggggght ! managed to get it working! I downloaded the PROBOOT.exe agent from intel created a bootable floppy disk and booted from it. Reset the network card and Feisty detected it! The only observation i had is that their is a high latency when u ping an IP. Any idea how to resolve this issue?

Rdgs,

H.

---

### Post by blenderfish on 2007-04-24
I am having the exact same issue with the system not seeing my wireless card.  I appear to have the same card you do.  Can you post specific instructions for what you did with ProBoot.exe to get this working?

---

### Post by hdotcom on 2007-05-25
Hi there,

Did u manage to get it resolved? If not follow the link below and you will find the steps you need. 
[http://ubuntuforums.org/showthread.php?t=409281&page=2](http://ubuntuforums.org/showthread.php?t=409281&page=2)

Rgds,

H,

---

