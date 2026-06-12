---
title: "I want to diable my Broadcom wireless"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by dreamsR4living on 2007-11-02
I am using a Broadcom Wireless card in my laptop, which is turned on by default. I want to turn it off when I'm not using it, because I use a wired network. I can enable or disable it with right clicking my Networkmanager. Do I really disable my wireless with that???

---

### Post by kevdog on 2007-11-02
I think the disabling the network card in network manager just bring the network card down (I dont think it turns it off).  Its equivalent to the folliowing command at the command line:

sudo ifconfig wlan0 down

If you really wanted to avoid turning it off everytime, you would blacklist the driver associated with the card within the /etc/modprobe.d/blacklist file.  The if you wanted to use the card you would activate with

sudo modprobe <driver>
sudo ifconifg <interface name> up

---

