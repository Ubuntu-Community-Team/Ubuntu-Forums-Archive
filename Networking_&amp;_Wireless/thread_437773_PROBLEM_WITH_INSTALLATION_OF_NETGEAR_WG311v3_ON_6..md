---
title: "PROBLEM WITH INSTALLATION OF NETGEAR WG311v3 ON 6.10"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by dimziou on 2007-05-09
I have recently installed ubuntu 6.10 and i can't install my wireless network card (NETGEAR WG311v3-MARVELL CHIPSET). I used the ndiswrapper utility (downloaded from the live-cd using synaptics package manager since my only exit to the internet is through this wireless network card). When i type "ndiswrapper -l" i get "Driver installed  Device present" but when i type "iwconfig" i get "no wireless extensions" and the card does not show up in system>administration>network (only a modem interface which showed up even before the ndiswrapper installation).
Please Help !!!

---

### Post by chrisbain88 on 2007-05-09
hey
i have found that i could not access wireless networks with that adapter either, as far as i can gather it is not a linux friendly wireless card (or windows 64bit either), i gave up on it
i have now brought a new laptop with the aethos adapter in it and works like a charm
chris

---

### Post by dpmccoy on 2007-05-09
This is odd.  I've been using the exact same card since this January with no problems at all.  I utilize the Windows drivers and ndiswrapper.  It works for me on Edgy and Feisty.  

Poster #1: Are you using networkmanager?  Did you install all of the ndiswrapper packages when you installed using Synaptic?

---

### Post by chrisbain88 on 2007-05-09
hey Dpmccoy
how did u get the ndiswrapper to work, can you please write a tutorial
i tried following one of the others but just ended up getting lost and it not working
cheers
chris

---

### Post by dpmccoy on 2007-05-09
> **chrisbain88 said:**
> hey Dpmccoy
how did u get the ndiswrapper to work, can you please write a tutorial
i tried following one of the others but just ended up getting lost and it not working
cheers
chris

I used an excellent post on the Ubuntu forums; I'll search for the right one, and give you link for it.  It is pretty easy and self-explanatory.  I hope I can help. :)

---

### Post by dpmccoy on 2007-05-09
> **chrisbain88 said:**
> hey Dpmccoy
how did u get the ndiswrapper to work, can you please write a tutorial
i tried following one of the others but just ended up getting lost and it not working
cheers
chris

I can't find the original post that I used to set up the card, but this one might work better:

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Two changes: I installed my ndiswrapper packages through Synaptic.  Make sure you install ndiswrapper-common and ndiswrapper-utils.  

I used the Windows XP Netgear WG311v3 drivers from my installation CD.  I did not use the Marvell drivers that the tutorial refers to.  

If this doesn't work for you, please let me know where you're getting stuck.  I'll check back.

---

### Post by gypsy_roadhog on 2007-05-11
I have had similar problems with this card. It worked fine for a while until I tried to change the config to access wpa rather than wep. After that the card would not accept any essid and kept reporting card not ready.

Clearly I had changed some setting on the card and this was preventing the linux software from working. (iwconfig reported that the essid had been changed but this did not actually happen).

After hours of trying I resorted to reinstalling windows on a spare corner of the machine and using the netgear windows software to configure the card.

On rebooting to Ubuntu the card works fine. I don't like it but it does work.

---

### Post by dimziou on 2007-05-31
Solved by upgrading to 7.04, updating immediately after installation, clean installation of ndiswrapper using synaptics package manager, installation of the windows xp driver through terminal (the ndiswrapper gtk did not install the driver - ndiswrapper -i), assigning the driver to the spesific pci device (lspci &lspci -n - ndiswrapper -a), loading module (modprobe ndiswrapper) and restarting.
Thank you all for your help !!!

---

