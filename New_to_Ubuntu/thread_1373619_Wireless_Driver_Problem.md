---
title: "Wireless Driver Problem"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by csinchicago on 2010-01-05
I recently installed Xubuntu (9.10) on my old laptop but can't get the wireless to work.  It recognizes my PCMCIA card, but under configuration it only says "latency=0".  The card is a Linksys WPC54G (v2), which according to the documentation at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA ]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA")it should work "out of the box".  

What else should I do or check?

Thanks in advance!

---

### Post by gordintoronto on 2010-01-06
Does the card show up when you run accessories/terminal and enter the command:
lspci

Is there a network icon up at the top-right of the screen near the volume control?  If so, right-click it, select "edit connections," pick the Wireless tab, then "add."  You will need to enter a name and your router's ID, encryption type and password.

---

### Post by csinchicago on 2010-01-06
The card shows up when I run the command lspci.  But nothing happens when I enter the SSID in the wireless connections.

---

### Post by bkratz on 2010-01-07
> **csinchicago said:**
> The card shows up when I run the command lspci.  But nothing happens when I enter the SSID in the wireless connections.

Also make sure that the device is turned on in the bios and if there are any key combinations or switches that they are "on".

you might also want to copy/paste the output of the following here

sudo lshw -C network

That is (LSHW in lowercase)

and 

sudo iwlist scan

---

