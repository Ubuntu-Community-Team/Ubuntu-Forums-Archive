---
title: "[SOLVED] Connecting to access point"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by waldron on 2008-02-23
I am running a dual boot system, Windows/XP and Ubuntu 7.10 with a USB Zonet ZEW2500P to connect to a D-Link DSL-GH604T wireless router with WEP encryption and MAC filtering control. There are no problems with access from Windows/XP, but I have been unable to get it working with Ubuntu. (I should say at this point I know very little about Ubuntu).

I have trawled through other threads on these forums for similar problems, and these are the results of some of those tests.

lshw –C network

shows the wireless interface as wlan0 with the correct serial (MAC address) and driver=ndiswrapper+rt2500usb driverversion=1.45+Railink,05/27/2004, 1.00.01

iwlist scan

shows   Cell 01    (my neighbours network)

             Cell 02   Address:   xx:xx:xx:xx:xx:xx   (address of my router)
                           ESSID:     MYNETWORK
                           Protocol:   IEEE 802.11b
                           Mode:       Managed

Iwconfig

Shows    ESSID   MYNETWORK
                           Access Point: Not Associated.


In Network Tools, I can see two entries for Wireless interface

The first entry is for (wlan0) and shows ‘not available’ for every item under Interface Information. Selecting ‘Configure’ for this entry shows the correct details for ESSID, password type, password and configuration (DHCP)

The second entry is for (wlan0:avahi) and the Interface information shows my hardware address (MAC) correctly  and State: Active. However, the ‘configure’ button shows “The interface does not exist”.

Any help would be much appreciated, thanks.

---

### Post by Hightide on 2008-02-23
Hi
Have you tried to connect without WEP and the MAC address?

Sometimes network manager doesn't work very well with WEP.   Try with WPA.

regards

:)

---

### Post by waldron on 2008-02-24
Thanks Hightide.

I also have XP on my desktop and Vista on a laptop. I struggled to get WEP working, so I am reluctant to experiment with WPA in case I lose access from the other systems. 

I don't have any spare PCI slots, and my wireless router is connected to the master socket, which is too far away for wired ethernet connection to be practical.

So unless I can get this USB connection working, it looks as if I shall have to abandon plans to move to Ubuntu.

---

### Post by update_manager on 2008-02-24
You may want to just stick with MAC filtering. 

WEP doesn't add much more protection ([http://www.google.com/search?hl=en&q=WEP+crack+windows%7Clinux+&btnG=Search]("http://www.google.com/search?hl=en&q=WEP+crack+windows%7Clinux+&btnG=Search")).

---

### Post by waldron on 2008-02-24
I decided to see whether I could start over again, so commented out the wlan0 entries in /etc/network/interfaces and rebooted.

The network came up straight away - the first time it has ever done so. I've no idea what the problem was, but I will be leaving it alone now that it works.

Many thanks for your help.

---

