---
title: "[SOLVED] Wireless solution - belkin wireless G universal range extender??"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by IanB2 on 2007-12-01
I'm looking for some practical advise, having invested much time and expense in trying to solve the problem of connecting a desktop onto my wireless network.

So far (after researching which USB adaptors to use) I have only managed some partial successes and before 'throwing in the towel' would like to try one more solution.

The belkin wireless G universal  range extender might be a way forward as I could use the LAN connection on the range extender to connect to my desktop, avoiding the need to use a USB adaptor.
Does this work??  Huh Has anyone managed to do this successfully??
I've e-mailed Belkin and am awaiting a reply.

History of my experiences with USB adaptors:
Edimax - only works with ubuntu 7.04 and only supports WEP
Netgear WG111v1 works with ndiswrapper but drops the signal at random and will not reconnect
Netgear WG111v3 works with ndiswrapper but will not support ANY form of security (WEP, WPA)

Do you have any recommendations as to which hardware might work?  Huh The problem is in purchasing a device with the right chip set. Can you recommend where to purchase the device from? (The Netgear WG111v3 was sold as a WG111v2, which according to the Ubuntu hardware list 'might' work 'out of the box'.)

Any ideas or help would be much appreciated.

---

### Post by elite_angel on 2007-12-01
Try LINKSYS...

NDISWRAPPER fits to it...



NCC-United Kingdom International Advanced Diploma #245842
Linux Registered User #437451
Senior DeMOLAY - PJC , PSC

"Ang mundo ay libro, iisang pahina lamang ang nakikita ng mga hindi naglalakbay"




---==_d@rk_@ngel_===---

---

### Post by kevdog on 2007-12-01
Any device that is supported by the madwifi drivers work out of the box.  sorry I can name specific brands.

---

### Post by virgo977virgo on 2007-12-02
with ubuntu 7.10 I use the us robotics 5423 usb dongle.

it works flawlessy. without ndiswrapper but with the zd1211rw driver ([http://www.linuxwireless.org/en/users/Devices/USB](http://www.linuxwireless.org/en/users/Devices/USB)).

link to 5423 info page:
- [http://www.usr.com/products/networking/wireless-product.asp?sku=USR805423](http://www.usr.com/products/networking/wireless-product.asp?sku=USR805423)

links to other wireless hardare supported by linux:
- [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
- [http://www.seattlewireless.net/index.cgi/HardwareComparison](http://www.seattlewireless.net/index.cgi/HardwareComparison)
- [http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html)
- [http://www.linuxwireless.org/en/users/Devices](http://www.linuxwireless.org/en/users/Devices)

---

### Post by stooshbunutu on 2008-04-10
> **IanB2 said:**
> Netgear WG111v3 works with ndiswrapper but will not support ANY form of security (WEP, WPA)


I'm afraid you are wrong about this. You just need to disable roaming and configure it manually via network manager

---

### Post by IanB2 on 2008-05-29
The release of Hardy Heron has solved the problem for me as all the wireless cards I own are now supported 'out of the box' which is fantastic. My lastest purchases were from thelinuxemporium.co.uk a usb, pci & pcmcia cards.

---

