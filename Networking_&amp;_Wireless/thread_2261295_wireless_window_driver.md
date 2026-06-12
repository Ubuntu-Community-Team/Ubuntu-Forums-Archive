---
title: "wireless window driver"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by ljcttech on 2015-01-17
I'm trying to install wireless using windows driver on Ubuntu 14.04l desktop.  I know I have used terminal type in Sudo to install driver using .INF or .INI  or both to install please help get wireless going. I'm using laptop HP dv8000 it AMD

---

### Post by Hadaka on 2015-01-17
Hi, you should not have to go to all that trouble
your computer usually uses a simple driver.
please copy and post the output of,,
```
lspci -nnk | egrep '0200|0280'
rfkill list all
```
thanks

---

### Post by ljcttech on 2015-01-18
I type  code you give me but I didn't see my wireless. If I type in it said Broadcom corp. MCM4318 CAN YOU TELL IT MEAN THANK-YOU

---

### Post by chili555 on 2015-01-18
> If I type in it said Broadcom corp. MCM4318 It said more than that and my friend Hadaka needs the details in order to proceed. Please provide the requested details.

---

### Post by ljcttech on 2015-01-19
Here what it said - hp@hp-Pavilion-dv8000-EZ581UA-ABA:~$ lspci -nnk | egrep '0200|0280'
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
hp@hp-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill list all
I would like get drive for it or help get wireless going.   Realtek  work  but I can't get going on Broadcom wireless. Please help !!!!Tthank-you

---

### Post by ljcttech on 2015-01-19
When I update it lost wireless drive now I have used cat5 go on internet. I would like try get wireless going or try get driver for Ubuntu thank-you help I need

---

### Post by Hadaka on 2015-01-19
Hi please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by ljcttech on 2015-01-19
Got working now thank-you  I when other website it tell me type this too 

sudo apt-get remove --purge bcmwl-kernel-source
[COLOR=#333333][FONT=UbuntuRegular]Let's be sure there are no blacklists:[/FONT][/COLOR]
gksudo gedit /etc/modprobe.d/blacklist.conf

I did this too 

sudo -i
echo b43  >>  /etc/modules
exit
[COLOR=#333333][FONT=UbuntuRegular]You should be all set.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]If you find you have a conflicting blacklist, please do:[/FONT][/COLOR]
gksudo gedit /etc/modprobe.d/blacklist.conf 
then reboot then it see it my wireless thank-you for the help

---

### Post by ljcttech on 2015-01-19
sudo apt-get remove --purge bcmwl-kernel-source
[COLOR=#333333][FONT=UbuntuRegular]Let's be sure there are no blacklists:[/FONT][/COLOR]
gksudo gedit /etc/modprobe.d/blacklist.conf

---

### Post by Hadaka on 2015-01-19
glad that worked for you, please mark your thread solved.

leave the /etc/modprobe.d/blacklist.conf file alone, it;s suppose
to be there

---

