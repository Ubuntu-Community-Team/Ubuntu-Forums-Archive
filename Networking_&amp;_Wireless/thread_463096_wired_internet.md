---
title: "wired internet"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by nbk_9 on 2007-06-03
I have broadcom(BCM5754) ethernet card but when I go to SYSTEM->ADMINISTRATION->NETWORKING I see only Modem connection(ppp). My ethernet connection is not displayed. I am newb and tried sevral options but still can not connect to internet. The wired connection works for other PC(XP) I have.


This is on ubuntu 6.06 for PC.

---

### Post by cantormath on 2007-06-03
> **nbk_9 said:**
> I have broadcom(BCM5754) ethernet card but when I go to SYSTEM->ADMINISTRATION->NETWORKING I see only Modem connection(ppp). My ethernet connection is not displayed. I am newb and tried sevral options but still can not connect to internet. The wired connection works for other PC(XP) I have.


This is on ubuntu 6.06 for PC.

If its a desktop, seriously, just go buy a 10 dollar non-broadcom card.  If a laptop, you may want to download module-assistant, I think its in the universe repos or on the CD, then use that to install the bcm5700 module....it might not be in your kernal........but hmmmm, you cant connect to the internet......yeah, again if its a desktop, get another card, if its a laptop, maybe get a wireless card, find a wireless connection at a coffee shop, and go the module assistant route.

Also, install the updates if you have not done that yet, that might fix the problem.

---

### Post by nbk_9 on 2007-06-03
This is for PC, A new PC rather with built in 1 gb ethernet, So ubuntu does not support broadcom or is it b cos the cd does not install the module by default. I have the cd but dont know how to install that particular module. 

Just FYI. Here is what I see when I type these commands

sudo lshw -C network
Password:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:efcf0000-efcfffff irq:10
__________________
 iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.
___________________
 sudo iwlist eth1 key
eth1      no encryption keys information.

---

### Post by cantormath on 2007-06-03
correction, broadcom does not support linux.  They refuse to write drivers for it so it is hard to reverse engineer things.  Module assistent may not be on the cd.  If you through cheap nic in the box, do the updates, use module assistant, and install the broadcom bcm5700-source - module source for Broadcom's bcm5700 ethernet driver, I think it might work.  

Its at least worth a shot.

---

