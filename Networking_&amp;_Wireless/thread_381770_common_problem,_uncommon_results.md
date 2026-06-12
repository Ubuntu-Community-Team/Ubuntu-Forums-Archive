---
title: "common problem, uncommon results"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Drate on 2007-03-11
*EDIT*
I originally posted this because I had forgotten a step in the following directions, but I found that step (the blacklist step), so now I hope it brings much joy, satisfaction, and working computers to anybody else with the same problems as me.

My nic, and I *assume* all other standard issue Wal-Mart Linksys Wireless-G with Speedboosters, have a Broadcom 4318 chipset... that is important, because THAT is the reason we blacklist.  I believe this is a unique step to these chipsets but would be interested to know what others have found.

I have a dual-boot XP/Edgy system, WMP54GS Linksys Wireless-G with Speedbooster wireless nic as my only *convenient* internet access.

What I did is this:

Packages Installed:
-------------------

wpasupplicant  (installed by default in Edgy)
ndiswrapper-common
ndiswrapper-utils-1.8
network-manager
network-manager-gnome

(plus whatever dependency packages it asks for)

################

# Installed windows drivers for network card:

# bcmwl5.sys
# WMP54GS.inf

sudo gedit /etc/modprobe.d/blacklist

#Added this line at the bottom:
blacklist bcm43xx

sudo ndiswrapper -i {path}/drivername.inf

ndiswrapper -m

sudo gedit /etc/default/wpasupplicant

#Added this line:
ENABLED=0

#Save and exit.

sudo nano /etc/iftab

#Commented out ("#") the line with the mac address
#Save and exit.

gedit /etc/network/interfaces

#Uncommented portion modified to look like this:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

#Save and exit.

#FOR FEISTY USERS... try this next thing as well... and let me know if it works... I'm not liking Feisty.
sudo modprobe -r bcm43xx

#Restart computer.

---

### Post by Drate on 2007-03-30
I am replying to myself so ppl won't think this was an unresolved issue while browsing for answers. :)

---

### Post by The Wanlorn on 2007-04-02
What else is in /etc/default/wpasupplicant besides the ENABLED =0 line?  I'm having issues connecting to the WPA protected network at home, and hopefully this fix will work.

---

### Post by Drate on 2007-04-02
Nothing else is in that file...

What's your card?  What kind of system do you have?  Let me know some details... maybe I can help.

I could also rewrite the instructions to be a little more "user friendly"...

Mostly just know that you can install those packages via Synaptic Package Manager under System>Adminstration.  And you put your driver files in a folder by themselves.

---

