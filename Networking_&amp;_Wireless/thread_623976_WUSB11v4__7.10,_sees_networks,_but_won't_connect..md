---
title: "WUSB11v4  7.10, sees networks, but won't connect."
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by dcast on 2007-11-26
Hi I just installed 7.10 on a previous Windows machine, card is aLinksys, USB  WUSB11v4, I installed the drivers using the packaged version of ndiswrapper. In network manager, the card is displayed and so are networks in the neighbourhood, including mine. Unfortunately I can't connect. Network manager displays that it is associated with my essid, but no go. I made my network unsecure to make it easier to debug. 

I am on my laptop right now that has wireless fine.

iwconfig displays the device and sometimes lists essid as "off/any" or it believes it is on one of my neighbours networks but isn't, because it is not receiving an IP from them according to ifconfig. Does anyone have any ideas?

---

### Post by g770 on 2007-12-01
I have the same problem..  Can associate with the router  but can't get IP addresses.  It tries to get an IPv6 address.  It's odd because I got the same usb wireless adaptor to work on edgy with ndiswrapper, so it must be that something broke it in Gutsy.  

Anyone know how to fix this?

---

### Post by SZF2001 on 2008-01-14
I'm having the same problem, but I also tried this in Feisty and it still wouldn't work.

PLEASE, SOMEONE, ANYONE, HELP!

---

### Post by rockbrawler884 on 2008-01-14
i am a noob to linux, but had a similar problem with my Hawking HWUG1 wireless adapter.  try connecting to the wireless network using command line.

network-manager was able to see the networks but not connect so i did the following commands

sudo ifconfig "ifname" down
sudo ifconfig "ifname" up
sudo iwconfig "ifname" essid "yourAPname" key "keyhere" mode Managed rate auto
sudo dhclient "ifname"

ifname - Wireless interface e.g. eth0, eth1, wlan0, etc...
youAPname - name of your wireless AP
keyhere - your WEP key (if 64bit WEP use the format xxxx-xxxx-xx)

see "man iwconfig" for more detail.

I hope that helps!

---

### Post by SZF2001 on 2008-01-14
Would anyone be willing to test my theory and see if it works with your cards?

[http://ubuntuforums.org/showthread.php?t=667570](http://ubuntuforums.org/showthread.php?t=667570)

I think I didn't install too many other packages dealing with Wifi, but I think I've come to realize that, in some cases, the Network Manager can be your worst enemy when it comes to WLAN stuff - and this particular card.

---

