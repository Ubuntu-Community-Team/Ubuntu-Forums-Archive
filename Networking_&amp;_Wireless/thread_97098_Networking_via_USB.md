---
title: "Networking via USB"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by pierre_s_rosen on 2005-11-30
I currently own two computers that I would like to network together using a cable modem and a router.  The newer custom built PC runs an Athlon64 3200 (has ethernet) and the older Gateway PC runs an Intel Pentium II 300Mhz (no ethernet card, USB 1.0 ports).

Problem 1:  Installing a cheap ethernet card isn't an option.  Last time I tried to install a card onto the Pentium II motherboard, I wasn't able to get the card in, since the proprietary board made it near impossible to get the card into the slot.  I ended up having a tech guy at Best Buy install the video card...who said that he had a hell of a time getting it in the slot.  Plus, I don't think there are any more slots for the ethernet card...soo...

Possible Solution:  Connecting the old computer to the internet router via a USB port.

Questions:  
1)  Can I connect to the internet using a USB 1.0 port using Ubuntu Linux?

2)  What routers work with Ubuntu that also come equipped with USB and 10/100 Ethernet switches?  

      (I am aware of the Linksys Etherfast Cable/DSL Router with USB and 3 port 10/100 Ethernet switch -- is this supported?)

3)  If I can connect via usb...I would need to run the usb cable through a preexisting hole in the wall...it is obviously not wide enough for me to push through the head of a usb cable...which means I will have to 'splice' the connector onto the wire?  Where can I find directions to do this?  And where can I buy a 30 to 50 foot usb wire?

4)  Can I/Do I/Should I resort to a wireless internet router and if so, which one?  I tried this solution once with the old computer using Windows 98 but usb 2.0 ports seemed to be needed, since the old 1.0 ports didn't provide enough power.

5)  Other solutions I am not thinking of?  (Firewire supported on motherboard...but no port...so not really an option.  Getting a second cable modem and paying an extra $30-$50 isnt worth it...external usb dial up modem? yuk.)

Thanks!

---

### Post by mips on 2005-11-30
Give me the exact Linksys model number please.
Who is your cable/ISP provider ?
What is your current modem & router brand/model ?

What you have in mind might work or it might not. The problem is you cannot always use the Eth & USB together but this is not always the case. Should you be able to use them together you will need some PPP client on the USB PC and you will most likely get an IP address on the WAN side so your traffic will be routed via the cable network, not exactly a LAN. Secondly the ISP might not allow concurrent PPP connections.

A simpler solution might be to look at a USB->Ethernet adapter.
[http://www.netgear.com/products/details/FA120.php](http://www.netgear.com/products/details/FA120.php)
[http://www.dlink.com/products/?model=DUB-E100](http://www.dlink.com/products/?model=DUB-E100)
[http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/)   (See section "**Ethernet Adapters**")
[http://www.linux-usb.org/devices.html](http://www.linux-usb.org/devices.html)

---

### Post by pierre_s_rosen on 2005-11-30
I like the simple solution!  Thanks.

---

