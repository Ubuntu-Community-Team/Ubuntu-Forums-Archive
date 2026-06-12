---
title: "Edgy Wireless"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by BHelts on 2007-03-29
Hello,
Let me start by saying that this has probably been answered before, but because I am new to linux I don't know if I am looking for a utility to help me or whether I need to set up my network settings differently.
The problem I am having is this:  I have no problem logging onto wireless networks, but when I restart my laptop, or go from work to home or vice versa, the laptop does not auto detect or auto log on to these wireless networks.  I am looking for something that would allow me to set up profiles for preferred wireless networks or would automatically scan for wireless networks and allow me to choose which one to log on to.  As it stands now, I need to configure my eth1 and manually type in the SSID.  Any help would be greatly appreciated.

---

### Post by bobswat on 2007-03-29
'

---

### Post by bkeithly on 2007-03-29
You can try 

wifi-radar

mixed reviews on that one.


or try:

iwscan list

from the command line.  But then you will have to go in to the card from the GUI or command line (/etc/network/interfaces) and manually add the network info.

HOpe that helps.

---

### Post by BHelts on 2007-03-29
Thank you very much, I will try wifi-radar.  At first glance it appears to be about what I am looking for.

---

