---
title: "hotplug vs. rc.xxx files"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by vinfred on 2006-11-23
Is there a reason why most postings recommend to get rt61 be up and running at boot time in editing rc.xxx files rather than  using hotplug mapping in /etc/network/interfaces ?

According to debian standard documentation, PCMCIA cards should be started with hotplug mapping, because the card manager is started after the network interfaces during boot sequence. (this was true at least for Breezy)

example of what I did for D-LINK DWL-G630 rev E1 (rt61 chipset) on Breezy. was still running with Dapper. I've not yet checked with Efty

# Put an alias to associate ra0 to rt61 module in any file in /etc/modprobe.d
sudo echo "alias ra0 rt61"> /etc/modprobe.d/rt61
#edit your /etc/network/interfaces after keeping a clean copy
cd /etc/network
sudo cp interfaces interfaces.sav
sudo gedit interfaces
# the mapping hotplug section should look like
mapping hotplug
script grep
map eth0
map ra0
# add the following line
iface ra0 inet dhcp #or iface ra0 inet your_ip
# if you've run the wireless tools GUI (system - administration - Network) you'll find a line with
auto ra0
# delete or comment out this line if your card is a PCMCIA card (avoid to try and start it before card manager is started)
# you don't need to add all these informations related to your SSID and key as everything is already defined into /etc/Wireless/RT61STA/rt61sta.dat
# save and exit

---

### Post by FrodoB on 2006-11-23
That sounds like Slackware users are writing those documents, as rc.xxx files are part of the normal Slackware way of doing things.

---

