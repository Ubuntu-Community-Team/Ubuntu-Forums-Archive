---
title: "Zyxel g-162 and acx drivers?"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Mikko777 on 2006-09-17
Has anyone got zyxel G-162 pccard wifimodem to work with the (texasinstruments) acx drivers?

I did manage to make this card work with uninstalling the acx drivers that come with ubuntu and using ndiswrapper but it often hangs when changing AP's or when booting / shutting down system...

So i figure the acx drivers would be better.

questions:

1.any1 got the above system working?
2.how? i managed to install the acx drivers and firmware but nothing...
3.where do i need to install the firmware?
4.how to troubleshoot wifi? ie how do i know where the problem is?
5.when i built a custom kernel the pcmcia card doesnt even powerup? what do i need to enable for pcmcia support or is it a module i need to load?

PS. Ubuntu/linux roxxors, so help a noob out ^^

Edit: Well managed to solve anything except the custom kernel problems.

Heres the answers to most of my questions:

Networking howto:

Remove ndiswrapper

Install acx drivers:

1:Link correct firmware to correct kernel version:

sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16

1.5:Or do this or both:

Append the line
options acx firmware_ver=1.2.1.34

to /etc/modprobe.d/options

so that the 1.2.1.34 firmware is used each time the acx module is loaded.

2:Load acx module:

sudo modprobe acx

3:Network settings: Either use network-manager or edit /etc/network/interfaces:

iface wlan0 inet dhcp
wireless_mode managed #working mode
wireless-essid B1KBCnet # essid (sid) of your network
wireless_nick RS101 #How you like to other se you
wireless_rate auto #Transfer rate auto, 1M...11M etc
wireless_txpower 10 #Txpower in dBm


###############

Other Commands:

lspci	#lists pci devices
ifdown eth0
ifup wlan0
iwlist scan 

/etc/modules	#list of modules to load on startup
sudo /etc/init.d/networking restart	#to restart networking

---

### Post by erq on 2006-10-22
Hi!
Have you managed to get your Zyxel-card working?

---

### Post by mrtrick on 2006-11-06
I'd like to know the same. I'm fighting with a g-302 currently.

---

