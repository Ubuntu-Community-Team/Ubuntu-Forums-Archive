---
title: "Wifi not detected on IBM X40 laptop (Atheros chipset)."
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by Hookheathen on 2007-06-11
Help please!
I am having a frustrating time enabling my wifi on my X40 notebook. I loaded on 6.10 and then downloaded by wire approx 169 update packages(!) including the linux restricted packages that contain the madwifi drivers, which I understand are relevant to this chipset, I was unable to detect in Synaptic "madwifi tools" to install, although they all have green boxes, so I know they have been downloaded and are there somewhere and need to be identified to be installed(?) Accordingly I am still unable to turn on the wifi. This is the detail I get when ifconfig is typed in terminal, (which does not come as a surprise):-

=================================

lo no wireless extensions.

irda0 no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"Linksys"
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:17 dBm Sensitivity=0/3
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm
Rx invalid nwid:73 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

=============================

Any help would be greatly appreciated. Thanks.

---

### Post by tturrisi on 2007-06-11
It's working!@
You are just not associated with your access point.
do this:

sudo gedit /etc/network/interfaces
edit the file by removing anything ath0 related and put in the bolded text below.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth1
#iface eth0 inet dhcp  

[b]iface ath0 inet dhcp
wireless-essid Linksys
auto ath0[/b]
```

Save the file.  The go to Statem > Administration > Networking > select ath0 device & press the Activate button.

---

### Post by Hookheathen on 2007-06-12
Thanks for the guidance.

The interfaces window in terminal did not need modifying and the instructions you listed in bold were present, so it looks as though everything is there - but not quite! 

On going into Network Tools, under network device I have the screenshot for Unknown interface (ath0) but I am unable to get the "Configure" button to highlight. I feel I am getting closer!

/media/disk/Screenshot.png

---

