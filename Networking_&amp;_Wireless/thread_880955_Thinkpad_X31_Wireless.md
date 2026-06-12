---
title: "Thinkpad X31 Wireless"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by jjarzabek on 2008-08-05
Have an older X31 with built-in wireless.  Was working up until updates ran today.  Now nothing - no wireless.  Devices are found successfully and the wireless network settings are in place but it's like it doesn't even know the wireless hardware is there.  Any ideas?

The system was updated to "Hardy Heron".
Before HH, wireless was fine.

---

### Post by chili555 on 2008-08-06
The X31 came with 4-5 different wireless cards. Which one do you have? Find out with:```
sudo lshw -C network
```Post back and we'll be glad to help.

---

### Post by jjarzabek on 2008-08-06
Here is what it shows:

[INDENT]PCI (sysfs)  
    *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:4c:d6:0b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.0.0.103 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
[/INDENT]
What's interesting, I ran a fresh install of 8.04.1 and the wireless works now but I need to change it back and forth from roaming mode so that the interface updates.  It doesn't remember the settings nor will it find any other broadcasted SSID's unless I toggle in and out of roaming mode.  It seems like it "forgets" it has wireless capabilities.  I need to do this everytime the machine is rebooted.

---

### Post by tennvic^ on 2008-08-09
Seams to be solved on [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=409247](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=409247)

Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

I have a similar pb after upgrading from gutsy.

tennvic

---

### Post by jjarzabek on 2008-08-11
I tried that fix from the other thread but that doesn't do much.  What's odd is that even after getting the wireless to work in the same session, after several hours it stops.  I know it is NOT a hardware problem because booting into Windows, everything is fine.

---

### Post by chili555 on 2008-08-11
Anybody see any issue here?> driver=**ath_pci** ip=10.0.0.103 And here:> # these aes modules break the **airo** driverI doubt the blacklist did anything useful.

---

### Post by craigtyson on 2009-04-20
Got a similar issue with my IBM X31 airo WIFI card on Gutsy (old but works well with the X31)

WIFI works then WIFI stops

do a 
sudo modprobe -r airo
sudo modprobe -i airo

then WIFI works again

Seems to be dependent on the amount of traffic put through the card so always stops in the middle of a film or large download

Anyone got any ideas?

---

