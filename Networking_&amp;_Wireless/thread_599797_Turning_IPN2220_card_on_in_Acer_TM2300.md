---
title: "Turning IPN2220 card on in Acer TM2300?"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by holleydc on 2007-11-01
Solved this by installing Ubuntu 7.10 with Gutsy Gibbon, then reinstalling IPN2220 drivers with ndiswrapper (the version included with Ubuntu 7.10 CD).

---

### Post by srasiroslayer on 2007-11-23
hello, i have a problem with the ipn2220
my laptop is an acer travelmate 2702 WLMI
after installing ndiswrapper-utils and ndiswrapper
and adding the .inf file to it (whole folder was present)

and doing ndiswrapper -l to make sure hardware is present,
then adding ndiswrapper to /etc/modules for it to work on boot,
i get the wireless card in the network-manager
but it cannot detect any wireless networks.
please help

P.S.: wireless button is on

---

### Post by srasiroslayer on 2007-11-23
ok here's the weird thing,
it cannot find any wireless networks but when connecting manually it works but doesn't show the correct signal strength.
i guess this should do for now.
cheers

---

### Post by michael003 on 2007-11-23
I helped my friend install Ubuntu Gutsy on his laptop, and he also has an Acer with an IPN2220 wireless chip. We managed to install ndiswrapper and the IPN2220 drivers, and the wireless interface was detected but no wireless networks were found (as described above).

We eventually go it working by installing the kernel from Feisty (version 2.6.20-16) and using the drivers for the Linksys WPC54Gv4. It didn't work very reliably however -- the connection kept freezing and had to be restarted. My friend eventually gave up on Ubuntu because of this.

---

