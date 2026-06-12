---
title: "Help With Atheros WLAN card"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Oli1122 on 2008-11-15
I have recently installed Ubuntu 8.04 and can connect to the internet via an Ethernet port, but cant through my wireless card (it was working before i upgraded from vista to Ubuntu) the model of the atheros Wi-Fi card is 
 
"atheros 802.11 Wireless LAN card"

Can anyone help me please???? :confused:

---

### Post by rynyeager on 2008-11-15
This is the thread that I used that got me up and running. Now I am trying to find out how I can connect to the wireless. I am having issues with the passphrase.

This is the information about my system and how I got my wireless card to work. I am using a 32 bit system. The following codes worked for Ubuntu 8.04 and 8.10.

Quote: (in terminal type the following)
**lshw -C network**
Quote:
(This should be output on terminal screen)
[B]WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1b:38:c8:1c:d2
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:05:00.0
logical name: wlan0
version: 01
serial: 00:1f:3a:04:bd:7a
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,05/02/2007,5.3.0.45 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 86:04:70:52:24:69
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/B]
Quote:
(Type each line individually, best to cope and paste from here to terminal)
[B]sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*
wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip[/B]
***_(remove the space between ftp &:, i.e. [ftp://)](ftp://))_***

(Next you will copy these to your terminal one by one)
[B]unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules[/B]
Then reboot and the card should work.
Last edited by acreech; 3 Days Ago at 12:19 AM.. Reason: update comands
acreech is offline Report Post   	Reply With Quote



This took about 15 minutes and worked on the first try

---

### Post by Oli1122 on 2008-11-15
what do i do with that i am a noob when it comes to Ubuntu and Linux???? :confused:

---

### Post by walkerk on 2008-11-15
He is suggesting using ndiswrapper and the Windows driver for the Atheros chipset. This is what I did to get mine working as well.

Open up a terminal. 

Install ndiswrapper from Ubuntu's repositories:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```

Download the Atheros driver
```
wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
```

Unzip the driver compressed file
```
sudo apt-get install unzip
```
```
unzip Wireless*
```
```
cd Atheros
```
```
unzip HR*
```

Blacklist the native driver
```
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

Stop the native module
```
sudo modprobe -r ath_pci
```

Install the driver with ndiswrapper
```
sudo ndiswrapper -i net5211.inf
```

Check if the driver is installed. You should see net5211 listed.
```
ndiswrapper -l
```

Start up the ndis module
```
sudo modprobe ndiswrapper
```

Now check for an AP. You should see yoru wireless network.
```
iwlist scanning
```

Now connect w/ NetworkManager, WICD, manually... I didn't double check that ftp link...

---

