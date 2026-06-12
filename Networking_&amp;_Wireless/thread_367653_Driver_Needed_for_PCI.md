---
title: "Driver Needed for PCI"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by madhucm on 2007-02-22
Hi,
i am not able to find driver for "Rsltek 8139D PCI Fast Ethernet driver" as i have older verison which doesnt work on ubuntu 6.06 since it uses kernal 2.6xx .... when i try to compile the source of that driver , dam it will throw lots of bugs..... can anyone give me latest version of that driver which works on my Ubuntu 6.06...

ThankYou

---

### Post by Jussi Kukkonen on 2007-02-22
Are you absolutely sure the driver is not included in the kernel? There are two drivers that seem to be close matches: 8139cp and 8139too

Normally, if a driver exists it's included.

---

### Post by madhucm on 2007-02-22
yes i'm sure its not installed . if it were installed it would automatically detect my ethernet card. and also i've cheked in network configuration, i couldn't find my ethernet card enabled and also i did ifcong stuff.... nothing works.... plz help me 
I love to work on ubuntu... 

Thank you

---

### Post by RomeReactor on 2007-02-23
Hi. If you have the cd that came with your wireless card, then use the win xp drivers with NdisWrapper. This is what the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#R") page has to say about it (look under the 6th item):

>    6. Card: Realtek 8139d (card manufactured by Silan Microelectronics)
          * Chipset: rtl8139d (Unknown Device 1904:8139)
          * Driver: ndiswrapper-utils ver:1.8.0ubuntu2 and driver provided for winxp in included cd
          * OS: ubuntu 6.06 LTS
          * procedure:
               1. ndiswrapper -i netslnt.inf
               2. ndiswrapper -d 1904:8139 netslnt
               3. ndiswrapper -m 
          *
          * reboot the system
          *
          * hope this works for u all

---

### Post by Jussi Kukkonen on 2007-02-23
> **madhucm said:**
> yes i'm sure its not installed . if it were installed it would automatically detect my ethernet card.

A driver being installed and a card being automatically detected are two different things -- the 8139too driver *may* work well, but as your card is not recognised (it's not in the pci id database on Ubuntu 6.06), it does not get used...

You could try *modprobe 8139too* (does this need the pci id database? no idea) and then configuring ethernet , but then again the ndis-solution above might be good enough for you...

---

### Post by madhucm on 2007-02-23
Hi
i've searced for ndiswrapper tool in internet ,but it says "Ndiswrapper is a Linux module which allows Ubuntu to use the Windows driver for wireless cards"
what you mentioned about ndiswrapper it is for wireless PCI....
But what i use is not wireless ... i 've installed my ethternet card in my pc, i've software driver which is givin for that ethernet card but its a older version , if i try to compile its source file it throws me hell lots of bugs :confused:  . and i'm using ubuntu 6.10 drapper. plz help me... 

ThankYou

---

### Post by RomeReactor on 2007-02-24
Is your computer a desktop system or laptop? If it's a desktop machine, did you install that card yourself, does it have integrated ethernet ports?

---

### Post by madhucm on 2007-02-24
i'm not using laptop... i have PCI slot in my pc... i've manually inserted ethernet card .... it works on xp coz i have installed drivers which is given in cd...
if i go to ubuntu , it doesnt detect my card , i've older version driver which dosen't support i hope so.
Help me plz.... :( 

ThankYou

---

### Post by RomeReactor on 2007-02-25
Look for the **integrated** ethernet ports on your pc's motherboard; practically all modern motherboards (those bought within the last 5 years, at least) have integrated ethernet ports, so try using those instead of the card you installed, and see if that works.

---

### Post by shreepads on 2007-07-04
Pls look at the last post on:
[http://ubuntuforums.org/showthread.php?t=483870](http://ubuntuforums.org/showthread.php?t=483870)

---

