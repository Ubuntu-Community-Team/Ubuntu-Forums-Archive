---
title: "Cannot Connect to WPA-PSK Network"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by Ertai88 on 2007-09-24
I'm sorry if there's an answer somewhere on this forum, but I've been searching for awhile and didn't see anything that could fix or help me.

First off, I'm running 7.04 Feisty. My wireless adapter is a DWL-G122 rev A2, with the drivers installed though ndiswrapper. It can connect to unprotected networks, but it doesn't seem like it can connect to my WPA-PSK home network. When connecting using Network Manager, the icon in the tray doesn't have any green orbs, and seems to hang at "Waiting for Network Key for the wireless network "Network"". And yes, I did enter my key properly.

I've tried using Wicd as well, but it hung at "Obtaining network address" or something similar to that.

Any help would be appreciated, 

-Ertai

---

### Post by kevdog on 2007-09-24
Make sure you have the wpasupplicant package installed ... sounds like you do.

Make sure the essid of the router is being broadcast without any funky letters or symbols and make sure there are no spaces inside the names

Try first with WPA1 PSK if you can.  Sometimes WPA2 is not supported by the drivers.

Ensure that the windows drivers you installed inside ndiswrapper actually support wpa.  Im not sure how old of card you have but if its really old, then it probably wont work.

Check the wicd log file out -- I think its in /opt/wicd/wicd.log or somewhere near this location.  It might be more descriptive telling us why you can not connect.

Lastly can you tell us the chipset of your device -- you can find this with 
lspci -nn 
if its not a USB device

Thanks

---

### Post by Ertai88 on 2007-09-24
Yup, wpasupplicant was the first thing I checked. Running sudo apt-get install wpasupplicant tells me its the newest version.

My ESSID is simply 8 letters with a period in it.

I'm not too sure what version of WPA I'm using, as on my router settings, it just says WPA-PSK. If this helps, I'm using the same drivers I used on Windows XP, and those could connect with no problems.

As to the Wicd log, I am actually no longer using it. I switched back to Network Manager as soon as I couldn't get it working.

The adapter is a USB device, so lspci -nn won't work for it. But on the [WirelessCardsSupported Page](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), it lists it as Prism (DWL-G122, rev A2)

Thanks.

-Ertai

//EDIT: Alright, I reinstalled Wicd. Here's a snippet of the log:

```
2007/09/24 20:06:00 :: setting wireless network 0 property automatic to value False
2007/09/24 20:06:29 :: setting wireless network 0 property ip to value 
2007/09/24 20:06:29 :: setting wireless network 0 property netmask to value 
2007/09/24 20:06:29 :: setting wireless network 0 property gateway to value 
2007/09/24 20:06:29 :: setting wireless network 0 property dns1 to value 
2007/09/24 20:06:29 :: setting wireless network 0 property dns2 to value 
2007/09/24 20:06:29 :: setting wireless network 0 property dns3 to value 
2007/09/24 20:06:29 :: setting wireless network 0 property enctype to value wpa
2007/09/24 20:06:29 :: setting wireless network 0 property key to value WPAKEYHERE
2007/09/24 20:06:29 :: setting network profile
2007/09/24 20:06:29 :: 100: Profile Written
2007/09/24 20:06:29 :: connecting to wireless network HHFV.NET
2007/09/24 20:06:29 :: 
```

---

### Post by Ertai88 on 2007-09-25
Bump!

Anyone have any suggestions?

---

### Post by kevdog on 2007-09-28
Can you take the period out of the ESSID?? Im not sure if you have access to the router but I would use only numbers and letters first.

How did you install drivers for your device??  RTL devices are tricky sometimes and not all support WPA.  Have you confirmed this device is WPA compatible?

---

### Post by Ertai88 on 2007-09-28
It's installed through Ndiswrapper. The device should be WPA compatible because it worked perfectly under Windows.

Removing the period doesn't help either.

---

