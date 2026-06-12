---
title: "BT Voyager 220v"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by godwine on 2008-10-12
About me: I've used MS-DOS 3.0 onwards up to XP. Twelve days ago I knew little of Ubuntu before I downloaded and installed it. Now I know a little more but – unfortunately – access to the internet has not been possible because of an ethernet failure. I've spent well over forty hours trying to troubleshoot my network and I feel that this initial hurdle may be too much for me to convert to Linux.

Anyroadup, my hardware consists of a Medion Athlon XP 3200+  dual booting PC with a PCI HP ANA-6911A=DEC 21143 (Tulip driver) ethernet card directly cabled to a BT Voyager 220v ADSL Broadband/Voice router with BCM6348 chipset. This outfit can easily access the internet in XP. I also know the network can work in Ubuntu because the Voyager ethernet LED is lit for 15secs on boot-up (in one configuration I managed to keep the light on all the time – but with no internet access). I've tried many ways of resolving the problem and I think I am now basically familiar with the commands, applications and terms below:

/etc/network/interfaces
/var/log/syslog
eth0-avahi
iface eth0 inet dhcp
ifconfig -a
lspci
Network
Network Tools
sudo /etc/networking/ restart
sudo gedit /etc/network/interfaces
sudo gedit /etc/resolve.conf
sudo ifconfig eth0 192.168.x.x netmask x.x.x.x up
sudo ifdown
sudo ifup
sudo pppoeconf
Synaptic

I've tried various approaches with appropriate re-configurations and re-boots:

re-installed Ubuntu 8.04
installed Ubuntu 6.10
re-installed Ubuntu 8.04
removed NetworkManager completely via Synaptic (suspicion of bug)
downloaded and added WICD via XP and Synaptic
removed WICD completely via Synaptic
ethernet cable plugged/unplugged
Router on/off
Router DHCP on/off
static IP on/off
gave up a USB eciadsl-usermode_0.12-1_i386.deb installation after three hours
installed openSUSE 11.0

Is there a method, website or thread that I've overlooked? Can anyone see what I couldn't after twelve days of trying to get Ubuntu to connect to the net?

Cheers

---

### Post by ianhaycox on 2008-10-13
After running ifup eth0 can you go to [http://192.168.1.1](http://192.168.1.1) in firefox to see the config page on your router?

Sounds dumb, but maybe you just need to enter your ISP username/password into the router config.

---

### Post by godwine on 2008-10-13
Thanks, I've tried that. There appears to be no connection between eth0 and my router -except briefly during boot. I've reconfigured the network and pinged for many an hour .....

What I thought I would do is start all over again, re-install Ubuntu (for the fourth time) and post relevant listings and try stepwise troubleshooting in a new thread.

I think it best to start listing: lshw -C network, lspci -nn,  ifconfig, /var/log/syslog, /etc/network/interfaces and so on.

Thanks for responding; it gives one hope.

---

