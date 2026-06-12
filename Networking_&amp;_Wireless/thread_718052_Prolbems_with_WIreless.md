---
title: "Prolbems with WIreless"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by rarara77 on 2008-03-07
Hello,
I am currently using the Everex Cloudbook, mini laptop with gOS.

I messed up my "interfaces" file and now I can't connect to a wireless network using the Network Mananger GUI.  I currently use ifconfig and iwconfig at terminal to connect to wireless networks.  However I would like to use a GUI.  Here is my current interfaces file:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan2
iface wlan2 inet dhcp

auto ath0
#iface ath0 inet dhcp

What must I do to be able to use a GUI to connect to wireless networks.
All of the networks I need to access use DHCP if that helps.

Please let me know if I have to do anything that might really break something.

Thank You Very Much

---

### Post by uberlube on 2008-03-07
1) What type of wireless card do you have?
2) You will have to set up you wireless card in the command line unfortunately (probably). But this can be quite painless if done the right way.

---

### Post by Paris Heng on 2008-03-07
> **rarara77 said:**
> Hello,
I am currently using the Everex Cloudbook, mini laptop with gOS.

I messed up my "interfaces" file and now I can't connect to a wireless network using the Network Mananger GUI.  I currently use ifconfig and iwconfig at terminal to connect to wireless networks.  However I would like to use a GUI.  Here is my current interfaces file:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan2
iface wlan2 inet dhcp

auto ath0
#iface ath0 inet dhcp

What must I do to be able to use a GUI to connect to wireless networks.
All of the networks I need to access use DHCP if that helps.

Please let me know if I have to do anything that might really break something.

Thank You Very Much

1st:
Yes what type of **driver** and **wifi card** you are using? The driver is the far most important that causing you cannot connect to wireless network. Check the compatibility.

2nd:
Make sure you have right driver, then just correct your configuration, in this case what is your wifi interface?

Check:
> iwconfig 

/etc/network/interfaces
> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan2
iface wlan2 inet dhcp

auto ath0
iface ath0 inet dhcp [COLOR="Red"]#uncomment it ,no harm[/COLOR]

Restart your network:
> /etc/init.d/networking restart

---

### Post by rarara77 on 2008-03-08
Well I can connect to wireless networks fine using:

sudo ifconfig wlan2 down
sudo dhclient -r wlan2
sudo ifconfig wlan2 up
sudo iwconfig wlan2 "MYSSID"
sudo iwconfig wlan2 mode Managed
sudo dhclient.

The problem is with the Network-Manager GUI program.  I uninstalled it to try and fix it.  Now to reinstall it I get the vague error that it basically will not install because it is missing required files.

---

### Post by sbphoto on 2008-03-13
I also bought an Everex Cloudbook and have had the same sort of problems. Beyond that, the software kept freezing up requiring a hard crash (battery removal because it would not take input from the keyboard, pointing device or on/off switch). There is no restoration disk or download now available. The gOS on the gOS site is not the same one on the Cloudbook and won't work. I am waiting for Everex to post a debugged gOS for download--nothing else seems to work.

It seems they rushed the product to market before the software was stable. Ug.

---

