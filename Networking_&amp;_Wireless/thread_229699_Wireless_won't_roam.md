---
title: "Wireless won't roam"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by Dave Klinzman on 2006-08-04
ATTENTION WIRELESS CONFIGURATION WIZARDS!

I have a Linksys wireless card installed in a Toshiba Satellite laptop running Ubuntu's very latest version of 6.06 LTS.  It works great with the AP installed at home.  However, when I take the laptop way from "home" it looses assoication with the AP (not surprising) but simply will not re-associate with anything else, managed, open, key or not.  I have tried using the Network Manager, terminal scripts, terminal commands individually, tried various config's at home that work and won't work to make sure I am not doing stupid (which I am sure I am somewhere.)

Here are some specifics:
Laptop wireless card: Linksys WPC54GS V1.1
I have configured this card using ndiswrapper and the latest driver available from Linksys.  

Wireless router: Linksys WRT54G Firmware Version: v2.02.2

Please keep in mind that everything works PERFECTLY at home.  The problem is when I travel, the laptop won't associate with any other AP's (and I've tried linksys, 2wire and netgear (all with no keys or encryption) without success.

Doing "sudo iwlist eth1 scan" will show AP's in the area with assoicated info.  When I turn off the key ("sudo iwconfig eht1 key off") then try and configure the essid ("sudo iwconfig eth1 essid WHATEVER") it just won't work.  I have found that the little network icon will go blue when successfully assoicated.  Of course, I can not to the "dhclient" command until I get assoicated with the AP, right?

When I change the AP at home to not use WEP and reconfigure the card appropriately, it re-associates with the AP immediately and works great. (I usually use WEP at home.)

Does ANYONE have any suggestions.  I have worked on trying to solve this for the last 5-7 days and am running out of options!!!!! :confused:

**Added after initial posting:**
I have done the following commands:
sudo ifconfig wlan0 up 
sudo iwconfig wlan0 key off
sudo iwconfig wlan0 essid "name of network" 
sudo dhclient wlan0 

They work great with the "home" router, not at all with anything else.

---

### Post by Dave Klinzman on 2006-08-10
Attention all wireless configuration experts - NEVER MIND.

I was able to determine that the GUI network manager writes info into the /etc/network/interfaces file when used to configure a WEP key for an interface.  This sets up perfect failure to assoicate to any other AP since the interfaces file is used to set up the network interfaces during the boot.

Solution was to comment out the lines added by the NM GUI and reboot.  The system then was willing to assoicate to any nearby AP and, if it wasn't set up with WEP, I connected with no further problem.

I also installed wifi-radar to use for those instances where more configuration info has to be specified for a connection (like my home connection with WEP.)  I still have the NM GUI installed but only for the icon info in the command line.  I don't use if for ANYTHING else!!!

Bottom line is to stay away from using the gnome NM GUI for any configuration requiring WEP as it will hose you for connectioning to any other AP!

---

