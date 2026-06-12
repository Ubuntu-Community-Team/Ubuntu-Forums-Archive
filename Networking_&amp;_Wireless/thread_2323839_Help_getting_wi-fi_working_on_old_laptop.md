---
title: "Help getting wi-fi working on old laptop"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by bobapplepie on 2016-05-08
I installed Lubuntu on an old windows xp era hp pavilion ze4600.  I added nm-applet to autostart applications, I enabled a proprietary driver, and I tried following these instructions ([http://askubuntu.com/questions/649662/lubuntu-15-04-broadcom-wi-fi-wont-work-at-all](http://askubuntu.com/questions/649662/lubuntu-15-04-broadcom-wi-fi-wont-work-at-all)), but the wifi still doesn't work.  Does anyone know how to fix it?

---

### Post by chili555 on 2016-05-08
Please start here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by bobapplepie on 2016-05-08
I read the post and ran the script.  I attatched the .txt file; I'm not very good/experienced at this so I have no idea what I should be looking for specifically. [ATTACH]268934[/ATTACH]

---

### Post by chili555 on 2016-05-08
> **bobapplepie said:**
> I read the post and ran the script.  I attatched the .txt file; I'm not very good/experienced at this so I have no idea what I should be looking for specifically. [ATTACH]268934[/ATTACH]Please check here:> ##### lspci #############################

00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
	Kernel driver in use: natsemi

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").I see not wireless card there; not PCI, not USB and not PCMCIA.

Are you sure you have one? Is it possible that it is no longer operational?

---

### Post by chili555 on 2016-05-08
This may be useful: [http://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Pavilion-ze4600-wireless-network-card-purchase/td-p/184535](http://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Pavilion-ze4600-wireless-network-card-purchase/td-p/184535)> There is a Mini_PCI slot at the bottom of the notebook to house the Mini_PCI Wireless card.

However, you need to check this slot by opening up this cover and to see if the antenna ( two wires ) are already installed or not. If you can see the antenna, then you are go to get a Mini_PCI wireless card from HP.You might open the cover and see if there is a card in there; something a bit like this but probably not exactly: [http://www.insidemylaptop.com/images/Compaq-Presario-2580US/replacing-laptop-keyboard-11.jpg](http://www.insidemylaptop.com/images/Compaq-Presario-2580US/replacing-laptop-keyboard-11.jpg)

---

### Post by bobapplepie on 2016-05-09
Alright, thanks for the reply.  I'm a bit busy right now but I'll try this later.

---

### Post by bobapplepie on 2016-05-10
As it turns out, the laptop didn't have wi-fi capabilities anyway.  Thanks for the help, though.

---

### Post by afz12 on 2016-05-12
Perhaps try a USB WiFi modem - TP-Link WN821 might work well and is inexpensive

---

