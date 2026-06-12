---
title: "How to enable / disable wireless interface (And of course disable the card as well)"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by NexusGS on 2008-10-11
Hi all,

I recently got a new PCI card for wireless network. My only problem is that i cannot see how can i disable (to be exact to "turn off" the card and renable when i need so. I don't want my wireless card to be on 24/7. I cannot figure out how to do it. Any ideas?

Thanx a lot!

---

### Post by lswb on 2008-10-11
Is this a desktop machine or a mini-pci card in a laptop? A laptop will usually have a switch of some kind, often a Fn-combo key. If it is a desktop and you just want to disable try 

sudo ifconfig eth1 down

 in a terminal, (substituting the correct interface name for eth1 if necessary). However, it's possible Network Manager or other networking software can overide this. A more reliable way would be to remove the driver module to disable the adapter. You would need to know the name of the driver module for the card, then

sudo modprobe -r module-name 

to remove, and 

sudo modprobe module-name

before using it again.

---

### Post by NexusGS on 2008-10-12
Thanx for your quick reply... But i would like something "easier", because the computer is not gonna be used by people who gonna be experienced enough to use the console...

---

### Post by iponeverything on 2008-10-12
Right click on network manager icon and uncheck "Enable wireless"

---

### Post by NexusGS on 2008-10-13
That option doesn't actually turns wireless card off, i think it just doesn't consider Wlan card as inactive, but i see that led in wlan card is on...Am i right?

P.S.: Thanx for the answers guys...

---

### Post by Uuxaul on 2011-07-30
How might one go about figuring out a module's name?

---

