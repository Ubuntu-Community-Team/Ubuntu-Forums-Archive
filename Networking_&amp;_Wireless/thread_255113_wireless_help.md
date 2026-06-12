---
title: "wireless help"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by Nodren on 2006-09-11
hey everyone, i dont know if this was already posted... i searched and couldnt find anything.

well anyway, i've recently installed Ubuntu onto my laptop.  I have a credit card wifi adaptor(D-Link DWL-630 C2)  and ubuntu finds it right away on boot, no problem there.  network manager also works well and i can use wpa encryption, no problem there either.

however, if i've already booted my laptop then plug in my card, i have to reboot to get it working.  i think i might be using madwifi.  i dont really know.  But is there any set of commands or something i can type so my card gets picked up after i boot my laptop?

---

### Post by tturrisi on 2006-09-11
post the results of these commands:
iwconfig
lspci

---

### Post by Nodren on 2006-09-14
heh when i ran the commands i actually managed to get a step further, i dont have the data handy now but if you still need it let me know.

anyway, apparently i had to restart the PCMCIA service before plugging in my pc card, so now it shows up when i do a lspci.... and if my wifi card is plugged in when i first boot the laptop i can remove it and plug it back in no problem.

however, if i boot it with out having the wifi card in, network manager doesnt see it.  i've tried killing it and starting it again and it doesnt change anything... modprobe shows the same modules loaded in either scenario. any ideas?

---

### Post by tturrisi on 2006-09-14
> **Nodren said:**
> however, if i boot it with out having the wifi card in, network manager doesnt see it.  i've tried killing it and starting it again and it doesnt change anything... modprobe shows the same modules loaded in either scenario. any ideas?
This is obvious because the card "is not there to be seen" by network-manager.
Put in the card and depending on your system it can take up to a minute for the card to be detected & the services started.

---

### Post by Nodren on 2006-09-14
i've waited about 15 minutes with the card loaded and network manager doesnt find it, even if i restart network manager.  it seems like theres a command i'm missing that'll let network manager scan for my new device.

---

### Post by tturrisi on 2006-09-14
Are you talking about net-admin or network-manager?  Net-admin is the applet that comes w/ ubuntu and network-manager is a separate utility that replaces net-admin. Net-admin = System > Administration > Networking

---

### Post by Nodren on 2006-09-14
network-manager, the tool to enable wpa on linux.  the standard net-admin doesnt do anything for wpa, and wpa is my goal.

net-admin does see ath0 if that helps.

---

### Post by Nodren on 2006-09-20
bump

---

