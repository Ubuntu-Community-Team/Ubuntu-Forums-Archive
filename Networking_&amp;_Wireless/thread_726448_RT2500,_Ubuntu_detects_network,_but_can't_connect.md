---
title: "RT2500, Ubuntu detects network, but can't connect"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by samc3 on 2008-03-16
Hi,

Sorry to post here, but I'm having real issues, and I've spent days trying to figure out the problem myself. 

I'm running Ubuntu 7.10, on 1.5ghz celeron M laptop that uses the RT2500 chipset for the built-in wireless. I've installed the latest nightly CVS of RT2500 from here, and followed numerous instructions from various sites, including the Ubuntu wiki on this. I've also installed RutilT. Basically I can see my network and detect it fine, but I can never connect to it, I just keep entering the passphrase and it repeatedly asks for it, and this doesn't matter if I enter the settings manually or select it from the network manager menu.

Also, things like ifconfig ra0 up show: no such device, modprobe rt2500 shows nothing, but modprobe rt2500.pci works. Ive also tried editing the etc/network/interfaces file, but no luck there either.

Ive got ubuntu working fine on my desktop and love it, so I'd really like it for the laptop too.

I would be really grateful for any help, cheers,

Sam

---

### Post by gordintoronto on 2008-03-16
This is a long shot...

Is it possible your router has been set up to only connect to a specific list of MAC IDs?

My network is set up that way, so the first step in connecting a new computer is to edit the list on the router.

Good luck,
Gord

---

### Post by samc3 on 2008-03-18
Hey,

Cheers for the reply, but that not the prob at all, something tio do with the drivers maybe?

Seems to be a recurrent problem with many people though...

Sam

---

### Post by dacorr on 2008-03-18
If i interpreted right it sounds like the laptop is detecting the network but will not connect and is not accepting the encryption key for the wireless network....

I had a similar issue on my laptop using he IPW2200 drivers and i went through the lot and it did not accept the key, i dropped it down to WEP and it was ok sounds like you use WPA though. Depending on the age of the onboard wireless it may not support the encryption type the wireless network is using.

I have had issues in the past where it would not handle encryption at all.

If you have the same problem you may need to drop encryption completely (better wireless performance as it does not have to handle encryption) but you will need to secure the wireless through MAC filtering and if the router allows binding MAC address to the Private IP and limiting the amount of private IPs available to use, 

Dacorr

---

