---
title: "wire shark &amp; madwifi drivers"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Blackcabs on 2008-06-28
Please can someone help. First of all WireShark  does not see any devices yet both my wired connection & my wireless con's can connect to the net.
Secondly i have just installed the Aircrack suite but Airmon-ng tells me it cannot put my card into monitor mode even though i have the correct madwifi drivers installed and running. I do have network manager running would this affect things ? 
please can you help as i have trawled through the various forums looking for an answer 
my card is a Netgear WPN311 with the Atheros 5212 chipset :confused:

---

### Post by kevdog on 2008-06-28
Can't use Network Manager at all for this -- Network Manager is built for everyday functionality -- not speciality cases such as yours.

You need to interact with the card through the command line.

Next bring down the ath0 (a virtual monitored mode interface to the physical device wifi0)

sudo ifconfig ath0 down

Create another virtual interface (in this example ath1 to exist in monitor mode):

sudo wlanconfig ath1 create wlandev wifi0 wlanmode monitor

Bring up the monitored mode interface

sudo ifconfig ath1 up

Although not specific for madwifi or wireshark, a basic tutorial guide is here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

