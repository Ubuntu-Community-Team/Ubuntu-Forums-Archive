---
title: "Acer 3680 Wireless not recognised"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by chrisbain88 on 2007-03-22
Hi all,
I have started uni and one of my units is using linux, I decided to install Ubuntu on my Acer Aspire 3860 laptop and it does not recognize my integrated wireless card.  Using the ldpci command it shows that it is present however in the network GUI section is only shows the modem and Ethernet.
Help is much appreciated.
Chris

---

### Post by Floppyjoe on 2007-03-22
What is the output of:
```
lspci
```
This will show you which network wifi card you have and you can proceed from there.

---

### Post by Hase on 2007-03-23
I've got the same laptop the thread starter does.  The relevant info from lspci is:

Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

The card is found and configured correctly using the Edgy live cd but once I install the system, it sees nothing.  No wireless entry in iwconfig, etc.  Anyone know why something works on the live-cd boot but not after install?

---

### Post by chrisbain88 on 2007-03-23
The output of lspci is
0000:0a:03.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

---

### Post by Floppyjoe on 2007-03-23
The first thing I would try to do is to use synaptic package manager to see if the linux-restricted-modules for your kernel is installed.
If it is not installed you can download it with synaptic if you have internet access.
If you don't have internet access you can use the Ubuntu install disk by clicking Synaptic/Package/Manager then click Edit/Add CDROM then click reload then search for linux-restricted-modules.

To find out your kernel version type uname -r at a terminal.

---

### Post by chrisbain88 on 2007-03-23
the linux kernal is 2.6.15-23-386

---

### Post by chrisbain88 on 2007-03-23
The problem has been solved, im not exactly sure what solved the problem but this is what i did, i did however follow instructions for another model card and downloaded updatesfor my linux
and the next morning it was working

---

### Post by xyz on 2007-03-28
> **chrisbain88 said:**
> The problem has been solved, im not exactly sure what solved the problem but this is what i did, i did however follow instructions for another model card and downloaded updatesfor my linux
and the next morning it was working

Which model was it if I may ask? Thnx.

---

### Post by chrisbain88 on 2007-07-02
im not entiely sure wat model card is in my laptop

---

