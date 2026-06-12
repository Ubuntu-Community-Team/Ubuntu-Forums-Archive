---
title: "LAN ethernet card no longer recognized"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by stepore on 2005-06-15
sorry for the cross-post to desktop support and networking.

I've got Ubuntu Hoary on an IBM Thinkpad with a built-in network card, which was working without any problems what so ever.

here's the thing; for the last 5 months or so i've been using a Netgear wireless card exclusively. In fact, I actually upgraded from Ubuntu Warty 4.10 to Hoary 5.04 using apt-get over the wireless. after upgrading i've been happily using the wireless card. yesterday, for the first time since the upgrade, i tried to plug a network cable (from the router) to the LAN card and it no longer works. it doesn't seem to even be recognized anymore. for some reason, during the update Ubuntu switched the card designations around. eth0 was the LAN card and eth1 was the wireless. but now eth0 is the wireless. i guess because it was plugged in at the time of the upgrade.

lspci shows this:
0000:00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)

lsmod | grep 3c59x
3c59x	    37160  0

in /etc/network/interfaces i've got this:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
name Ethernet LAN card

iface eth0 inet static
name Wireless LAN card
wireless_essid xxxxxxxxx
wireless_key xxxxxxxxxx
wireless_mode Managed
wireless_rate 54M auto
address 192.168.2.100

what's left to do to get the LAN card to be recognized? is it a hardware detection problem, caused by the upgrade, or just something i'm missing in a configuration file? the wireless works fine, as eth0. i've tried swapping the cards around (wireless as eth1 and LAN card as eth0) but it didn't work. 

ubuntu's network-admin tool only shows the wireless card and the built-in modem. there's no 'add device' option to the gui tool.

tips on what i can do to get the LAN card to work?

---

### Post by spd106 on 2005-06-15
Hi, I notice that you don't have the line "auto eth0" in your interfaces file.

You will need to bring down the connections before you make any changes. Then add the line.
You may also want to add hotplugging for your cardbus network card. Look in the man pages or this web site for more information
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/HOTPLUG.txt](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/HOTPLUG.txt)

good luck

---

### Post by kleeman on 2005-06-15
Hmm it looks like /etc/network/interfaces is assigning eth1 to your wire nic and eth0 to your wireless. It also looks like the wire nic module is being loaded. What does

dmesg | grep eth

show?

How about 

sudo dhclient eth1

Can you pull out your wireless connection (PCMCIA card)? This might help in debugging

---

### Post by stepore on 2005-06-16
[QUOTE=spd106]Hi, I notice that you don't have the line "auto eth0" in your interfaces file.
[/QUOTE]

ya - sorry about that. i didn't post the entire interfaces file. i have the 'auto eth0' at the very end of the eth0 (wireless) options. so, that's not the problem. but thanks for replying, i've only had one or two responses to 4 or 5 other problems i've posted here.

---

### Post by stepore on 2005-06-16
> Hmm it looks like /etc/network/interfaces is assigning eth1 to your wire nic and eth0 to your wireless. It also looks like the wire nic module is being loaded.
yup, i said that. eth0 was wired nic and eth1 was wireless card. but after upgrading to hoary (using the wireless card) the wireless became eth0. i've tried swapping the eth0 and eth1 in the interfaces script but then neither card works. so i have to keep eth0 for wireless to at least have the wireless working. and yes, the wired nic module is still being loaded but for some reason it's not getting recognized or used.
> What does dmesg | grep eth show?
nothing for eth1 (wired), just eht0 (wireless) stuff:
eth0: islpci_close ()
eth0: resetting device...
eth0: uploading firmware...
eth0: firmware version: 1.0.4.3
eth0: firmware upload complete
eth0: interface reset complete
eth0: no IPv6 routers present
>  How about sudo dhclient eth1 
tried that before too. it would finish with a failed to assign ip error.
> Can you pull out your wireless connection (PCMCIA card)? This might help in debugging
yes, everything i've tried to this point has been with the wireless card out.
thanks for your help.

---

### Post by stepore on 2005-06-16
so -- on the off chance it is a hardware detection issue. how does ubuntu search for *new* hardware. i mean, what would happen if i had ubuntu on a desktop and i installed a new NIC card. how does the system recognize it? more to the point, why doesn't the network-admin tool have an "add new device" option? i'm pretty damn sure that ubuntu warty had this option. how does one delete or add a new NIC or any other piece of hardware?

---

### Post by kleeman on 2005-06-16
Well you have the module for the wired nic loaded so that is good  :smile:  :smile: 
What happens if you try to bring the interface up with
sudo ifconfig eth1 up
Hopefully it won't lock up  ;-) 

also what does ifconfig by itself show?

I had a problem with an nic (driver in hoary broken) and what I did was

a) Compile driver
b) Load it with sudo modprobe DRIVER
c) Bring up the interface with sudo ifconfig eth# up
d) Get a dhcp address with sudo dhclient eth#

---

### Post by spd106 on 2005-06-16
The web page I listed above has some useful information, it mainly deals with wireless cards but there is a large overlap with cable-based networking as well.

ie look in /etc/iftab for listing of currently used nics.

It might take a while to read through and it's not written as a step-by-step guide. It might give you some places to look though.

You may want to try adding something like this to the interfaces file

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1
```
I also remember someone saying that they had this trouble and to solve it they removed some network managing app that they'd been trying out.

Good luck

---

### Post by stepore on 2005-06-17
> Well you have the module for the wired nic loaded so that is good
What happens if you try to bring the interface up with sudo ifconfig eth1 up
Hopefully it won't lock up
root@ubuntu-shine:/etc/network # ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
> also what does ifconfig by itself show?
it only shows lo statistics. nothing for eth1.
> c) Bring up the interface with sudo ifconfig eth# up
d) Get a dhcp address with sudo dhclient eth#
root@ubuntu-shine:/etc/network # ifup eth1
sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.

root@ubuntu-shine:/etc/network # dhclient eth1
sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device

this is so unbelievable. i booted up using the linux system rescue CD and it recognized the wired NIC no problem, set it up with DHCP and got an IP address. but ubuntu fails to see it.

WTF! i can't believe that i'm going to have to reinstall for something so minor as a network card! a card that was working at one time. surely there must be something to do.

---

### Post by stepore on 2005-06-17
> The web page I listed above has some useful information, it mainly deals with wireless cards but there is a large overlap with cable-based networking as well.
ya - i'm still going through that web page, it's pretty long. but i don't think it'll help because i've commented out the eth0 (wireless nic) stuff in /etc/networking/interfaces and just kept the eth1 (wired nic) and it's not working. even setting up the wired nic as eth0, nothing.
> ie look in /etc/iftab for listing of currently used nics.
it only listed the wirless card, but i added the wired nic card. still nothing.

> You may want to try adding something like this to the interfaces file

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1
```

tried that too. didn't work either. thanks for the help.

---

### Post by kleeman on 2005-06-17
Well if sudo ifconfig eth1 up did not work and the card is recognized by another linux system then that strongly suggests a driver issue. FWIW I had a similar problem with a Yukon Gigabit nic (works with warty FC2 etc but not with hoary, FC3, Latest Knoppix). What happened was that the kernel driver for my nic was broken in the kernels after 2.6.8. I did two things:

1) Went to the vendor's website (Sk98connect) downloaded the driver kit for linux and recompiled. This is what I am using right now in fact  :) 

2) Went to the Ubuntu bugzilla and reported my problem as a bug. The kernel dev (Fabbione) responded and the latest is that the bug will be fixed in breezy.

If you are community minded  :smile:  :smile:  lodge a bug report and see what happens...

---

### Post by stepore on 2005-06-17
[QUOTE=kleeman]Well if sudo ifconfig eth1 up did not work and the card is recognized by another linux system then that strongly suggests a driver issue. FWIW I had a similar problem with a Yukon Gigabit nic (works with warty FC2 etc but not with hoary, FC3, Latest Knoppix). What happened was that the kernel driver for my nic was broken in the kernels after 2.6.8. I did two things:

1) Went to the vendor's website (Sk98connect) downloaded the driver kit for linux and recompiled. This is what I am using right now in fact  :) 

2) Went to the Ubuntu bugzilla and reported my problem as a bug. The kernel dev (Fabbione) responded and the latest is that the bug will be fixed in breezy.

If you are community minded  :smile:  :smile:  lodge a bug report and see what happens...[/QUOTE]
 I guess a bug report is what i'll do then.

---

### Post by Poldi on 2005-07-01
it seems that later 2.6.x kernels broke support for this specific 3com card.

take a look here:
[http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized](http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized)

kind regards,
Carsten

---

