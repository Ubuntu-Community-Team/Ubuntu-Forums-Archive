---
title: "Airlink MIMO PCI Causes Lock-up"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by Orion2014 on 2006-11-29
Ok, 

I really want to get back to using ubuntu, but here is what is stopping me. 

I have my desktop on a wireless LAN because there is no phone jack where i have my PC set up, and not one anywhere NEAR it to be exact.

I have an Airlink MIMO card installed, which works fine in windows ONLY after i have installed the special included driver for it.

However, after several attempts to make it work in ubuntu 6.06, i have given up. It picks up FINE on the Live CD, but after install and reboot, it locks up the PC at the "configuring network devices" thing on the boot screen of ubuntu. It never goes away from that.

Any tips?

---

### Post by FrodoB on 2006-11-29
Publish the output of:

lspci

and the content of:

/etc/network/interfaces 

and someone may be able to assist.

---

### Post by Orion2014 on 2006-11-29
Can i do this while ubuntu is in "live" mode?

---

### Post by FrodoB on 2006-11-29
Well;

lspci 

would still be useful.

---

### Post by Orion2014 on 2006-11-30
Ok, I will boot up the live CD when i get home and post the results of running lspci

EDIT, well ive decided to just use VMware to run linux on my computer. Since it dosent like my network card, its the only option i have.

---

