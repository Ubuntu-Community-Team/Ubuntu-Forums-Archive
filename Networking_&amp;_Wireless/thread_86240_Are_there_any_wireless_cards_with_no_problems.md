---
title: "Are there any wireless cards with no problems?"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2005-11-04
Hi,
I am getting frustrated with ndiswrapper , WIndows Wireless Drivers etc.
To keep it simple, has anyone a wireless card and/or USB wireless device that did work out of the package with Breezy?

Right now I am willing to buy something new, as long as it will work!

MightyMouse

---

### Post by Kyral on 2005-11-04
I don't know what kind it is, but the wireless cards built in to Thinkpads seem to work.

But I have an Orinico wireless card in my Desktop that worked with the default Ubuntu Kernel (I rolled my own and forgot which module the driver was in so it doesn't ATM ;)

But avoid Broadcom chipsets like the plauge

---

### Post by landotter on 2005-11-04
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

I got the Netgear WG311T on sale for $40USD and it worked automatically upon reboot--I believe the WG511T for notebooks is equally as painless.

---

### Post by unkemptwolf on 2005-11-04
I was in the same boat as you about 6 months ago. I had a broadcom card that came with my laptop, and it was a pain to configure. Frustrated, I decided to replace it with this a Intel 2195ABG (ironic, since my laptop is a Presario 2195us, but I digress...). It works like a charm. I installed breezy yesterday, and I was able to connect to a network during the install. Once I was in, I got networkManager working (about 30sec worth of work), and now I have full Wireless capabilities.  I would reccomend it unconditionally.

---

### Post by Agent86 on 2005-11-05
Based on my experience with the Foxconn WLL-3350 PCI wireless card, adapters based on the Ralink RT2500 chipset are great.

Breezy detected the card "Out-Of-The-Box," and all it took to get WPA-PSK working was adding 8 lines to a text file, activating/configuring the card using the System > Administration > Networking tool, and a single reboot. 

No ndiswrapper, no wpa_supplicant.

This post/thread shows how to edit your /etc/network/interfaces file to enable WPA for RT2500 cards:

[http://ubuntuforums.org/showpost.php?p=430726&postcount=6](http://ubuntuforums.org/showpost.php?p=430726&postcount=6)

The store that I purchased my Foxconn card from is out of stock, but here is a list of other RT2500 chipset cards:

[http://ralink.rapla.net/](http://ralink.rapla.net/)

Note that the Belkin and Linksys models use the RT2500 chipset only on certain hardware versions, so these cards are not your best choice if you buy online (where you have no control over the hardware version of the card you receive).

---

### Post by MightyMouse on 2005-11-06
Thanks for all the input, I definetly have a few more options to try to figure out how to continue.

Thanks!!!!!

---

### Post by 23meg on 2005-11-06
My IPW2200 (Sonoma integrated) worked out of the box, I haven't had to configure anything at all, and I've never had any problems with it. In terms of autodetection Intel seems to be a GoodThing.

---

### Post by MightyMouse on 2005-11-06
I found an working howto by "remmelt", (praise to him) for my SMC2802w card.!!!!!

[http://ubuntuforums.org/showthread.php?t=27916](http://ubuntuforums.org/showthread.php?t=27916)

MightyMouse

---

### Post by hajk on 2005-11-20
Just bought the Netgear WG511T PC Cardbus. This card needs the madwifi driver from the linux-restricted-modules package (I use the 686 version), which is not installed in Breezy by default. This setup works fine without any need to recompile the driver---it was apparently updated in Breezy from the Hoary version, so the earlier part of this thread is now only of use to people still using Hoary...

I also use the network-manager package (and the nm-applet) to setup my network automatically, be it wired or wireless. No complaints there, either.:p

---

### Post by gexla on 2005-11-20
Check out my post...

[http://ubuntuforums.org/showthread.php?t=92569](http://ubuntuforums.org/showthread.php?t=92569)

Guaranteed, no problems with wireless.  All you need is a working ethernet card which should be much easier to get working than a wireless card.

---

