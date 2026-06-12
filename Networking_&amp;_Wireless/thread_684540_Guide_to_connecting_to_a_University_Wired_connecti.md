---
title: "Guide to connecting to a University Wired connection with 802.1x authentication."
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by jmar71n on 2008-02-01
I've noticed that there is little information 802.1x authentication on wired networks so i thought I'd write this post...

I'm at Aberystwyth University, they use;

IEEE 802.1x
PEAP
MSCHAP v2 authentication method
+ login with a username and password is required.
also the MAC address of the NIC has to be registered with the Uni

This method should work on all UK Uni networks, and has been tested on Ubuntu, Debian

Make sure you have registered your MAC address before continuing.

I'll be using wpa_supplicant as it is installed by default on most distributions.

OK so 1st

create a configuration file for wpa_supplicant, start up Terminal and....

# sudo gedit /etc/wpa_supplicant/wired.conf

then add to it;

#######################################

ctrl_interface=/var/run/wpasupplicant
ctrl_interface_group=your_group_name
ap_scan=0

network={
	key_mgmt=IEEE8021X
	eap=PEAP
	identity="....@aber.ac.uk"
	password="your_password"
	phase1="peaplabel=0"
	phase2="auth=MSCHAPV2"
}

#######################################
(replacing "your_group_name" with the main user name in Ubuntu.
                 "....@aber.ac.uk" & "your_password", leaving the quotation )

2/
then test your configuration by using the command

# sudo wpa_supplicant -ieth0 -Dwired -c/etc/wpa_supplicant/wired.conf -B; sudo dhclient eth0

replacing "eth0" with your wired adapter name as needed

If that works you will be assigned an ip address starting with 144.124 (at Aber) and you will be able to connect to the internet using the proxy settings (needed at aber). If it doesn't check the configuration file for any mistakes.

3/ 
Finaly to make wpa_supplicant start when your network comes up, or plug in the LAN cable it will automatically log on to you Uni network

# sudo gedit /etc/network/interfaces

Then edit this file so it looks something like this;
#######################################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -ieth0 -Dwired -c/etc/wpa_supplicant/wired.conf -B
post-down killall -q wpa_supplicant

#######################################

in my case eth0 being the network adapter connected to the Uni network.


Note// to restart you network services after you have edited  '/etc/network/interfaces' use the command

# sudo /etc/init.d/networking restart


And thats it, now every time you computer starts, or plug in the LAN cable (if your using a laptop)  it will automatically log on to you Uni network. Also these settings will not interfere with connecting to an non protected network, so that when you go home it will just work as normal with no alteratilons needed.

Hope this guide can help out a few people, unfortunately as far as i know there is no easy way with this.

---

### Post by mayahustle on 2008-02-03
I go to the University of New Orleans.  They have a similar setup I think.  They don't use MSCHAP v2 though, so I just left phase 2 as an empty string and everything else worked fine.  Thanks!

---

### Post by viciouslime on 2008-02-20
Anybody at The University of York can use the deb file i've created at [http://www.viciouslime.co.uk/downloads/doc_details/19-university-of-york-nas]("http://www.viciouslime.co.uk/downloads/doc_details/19-university-of-york-nas")

This might well work for other Unis too!

---

