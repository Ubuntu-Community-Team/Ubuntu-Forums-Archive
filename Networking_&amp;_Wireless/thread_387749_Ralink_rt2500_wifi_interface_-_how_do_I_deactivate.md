---
title: "Ralink rt2500 wifi interface - how do I deactivate on boot?"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2007-03-18
I have the following in my /etc/network/interfaces file and I can start my wifi connection without having to bother with RaConfig.  RaConfig is at times inconvenient to use.  Only the lines pertaining to ra0 are shown below.  I also have an ethernet interface.

iface ra0 inet dhcp
 pre-up ifconfig ra0 up
 pre-up iwconfig ra0 essid myid
 pre-up iwconfig ra0 channel 7
 pre-up iwpriv ra0 set AuthMode=WPAPSK
 pre-up iwpriv ra0 set EncrypType=TKIP
 pre-up iwpriv ra0 set WPAPSK="mypassword"

The problem I have is that when I boot the laptop, the wifi light comes on on the laptop, on and off and I do not want the wifi to come on at boot time.  I want the ethernet to come on only, but both Eth0 and ra0 are enabled in KDE's network settings when the machine boots and I have to go to the settings and disable ra0 every time I start the laptop.  Is there a way to automate this?  I am running kubuntu Edgy and I have put 'ifdown ra0' in my /etc/init.d/bootmisc.sh and the command is executed but does not solve the problem.

I have two profiles in my network settings but I do not see a way to make one the default profile.
One of the profiles is my LAN profile and the other is wifi and I want to make the LAN profile the default if that is possible.

When I want to use wifi I just activate the wifi profile and it connects.  I thought I would need to go to the command line and issue 'sudo ifup ra0' but this is not necessary.

thanks for any help or ideas

---

### Post by Pollywoggy on 2007-03-18
I thought this problem was related to KDE, so I disabled KDM and rebooted the machine, but the same thing happens, so it is not KDE.  I will have to look at the boot scripts to find where this is happening.

---

