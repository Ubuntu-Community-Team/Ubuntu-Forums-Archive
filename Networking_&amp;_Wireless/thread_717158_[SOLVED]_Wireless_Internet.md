---
title: "[SOLVED] Wireless Internet"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-03-06
Hi,
I have a wireless d-link dwl g122 usb adapter (version c1). I ran the command

sudo lshw -C network

at the end of the output it says this:

       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

It does not mention drivers. I can still get online but my internet connection is very unstable.

I just want the best method to install network drivers.

Thank you.

---

### Post by Hightide on 2008-03-07
HI Rytron

there is some information about your card in the  Ubuntu [wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

can you post full output of the C- network command?

regards

:)

---

### Post by Rytron on 2008-03-07
'myusername'@'computername':~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 'my mac address'
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by SunnyRabbiera on 2008-03-07
ndiswrapper usually does a good job with stuff like this

---

### Post by Rytron on 2008-03-19
XP is required to access stable wireless connection via d-link dwl-g122 usb wireless driver h/w version:c1 f/w ver:3.00
Ok, I have tried many methods found on Ubuntu forums and other sites. If anyone has properly installed windows drivers for a 'd-link dwl-g122 usb wireless driver h/w version:c1 f/w ver:3.00' **PLEASE **post here the exact way to do this. It is driving me up the walls. I have the Windows Cd with the Drivers.

If someone has the exact same usb adapter as me and downloaded the drivers - it would be great if I could following the same method.

I am totally addled. This is the only but major downfall of Ubuntu Linux.

do I need to blacklist default windows driver?

:confused:

---

### Post by Rytron on 2008-03-22
I have downloaded these drivers:

D-Link DWL-G122 Driver 1.13

from 

[http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/D-Link-DWL-G12-2Driver-113.shtml]("http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/D-Link-DWL-G12-2Driver-113.shtml")

Could someone please help me set up my wireless connection?

---

### Post by Rytron on 2008-04-19
Hi,
Often when I use wireless internet it cuts.
I notice that when I unplug my wireless usb adapter and plug it back in, I can then reconnect to the internet. While this may wear the usb connector, is there a terminal command to disconnect my wireless adapter and then reconnect it?
Thanks.

---

### Post by Rytron on 2008-04-26
I got my wireless cd installed on my Xp partition.
I copied all the .sys and .inf files to a folder.
Using the wireless network drivers tool under system>administration I tryed all the .inf files until one worked. It now says hardware present: yes with dr71wu.inf being used.

My wireless connection is now very stable.

---

