---
title: "Small IPW2200 problem (newbie)"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by uglefar on 2006-11-03
Hi 

I can't get my IPW2200 internal wireless card to show up in "Network Settings" as enabled and working even though it seems that the card is working. In network settings it says that the network interface isn't configured, and when i go into properties and try to enable it nothing happens. Do I have to install the ipw2200 drivers from sourceforge or is there an easier way?

When I type "lsmod | grep ipw2200" i get:
ipw2200               115652  0 
ieee80211              35272  1 ipw2200

And with "dmesg | grep ipw2200" i get:
[17179587.576000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179587.576000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179587.576000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179588.324000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179588.532000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.1

When I type in iwconfig the card turns up as eth1 and actually connects to the nearest access point. (From what I can read)

eth1      IEEE 802.11g  ESSID:"3Com"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 01:02:03:04:05:06   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/100  Signal level=-64 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

How can i get it to work in the network settings window?

---

### Post by subzero79 on 2006-11-03
ipw2200 drivers are included in the kernel. If you installaled ubuntu the should be enabled by default. If the driver was not loaded try:

sudo modprobe ipw2200

Then access Networking in System-> Admin to configure the interface.

In the properties of the network interface you can select your preferred network. Try using network-manager

sudo apt-get install network-manager network-manager-gnome

---

### Post by uglefar on 2006-11-04
Thanks for the quick answer :)

I tried sudo modprobe ipw2200 , but it is still not possible to configure the wireless nic in system-admin-networking. I installed networkmanager and it came up in the taskbar.

When I click it, it will only show the wired network.

I have made sure that the wireless card is on when I start my PC and Ubuntu edgy (I've got a button for that on my laptop)

---

### Post by subzero79 on 2006-11-04
Strange, just yesterday i was playing in live mode cd with a laptop with an IPW2200 card and it worked out of the box. It was a pavillion DV4000

Play around with the network interfaces.

First restart networking

sudo /etc/init.d/networking restart

assuming 

eth0 -> wired
eth1 -> wireless

try,
ifdown eth0
ifup eth1

BTW the router is configured by DHCP right?

Also check this...when you open "network" in system, it always display which eth is using. Place over it an write eth1 if eth0 is displaying. Then descativate the wired interface.

---

