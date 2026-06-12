---
title: "More RT2500 Trouble"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by bleachlizard on 2006-08-08
Newbie to Ubuntu looking for help... likes long walks on the beach...

I know that this topic has been thoroughly exhausted... believe me I didn't want to post a new topic about this, but pretty much nothing has helped at all on any forum that I've been on.  I have Breezy and a Ralink rt2500 chipset for my wireless card.  Supposedly Breezy comes with the drivers, but I'm not really sure if they're loaded or not.  I'm assuming they are loaded since it shows up in my network as ra0 and Breezy recognizes it in the device drivers.  I am on a college wireless network that requires WPA encryption.  Now, is it TKIP or AEP?  I really couldn't tell you that much.  I'm assuming that I'm just not configuring the connection correctly, although I have no way of testing if it's even discovering the signal.  All suggestions are welcome with an open ear. [-o<

---

### Post by [Rui] on 2006-08-08
Unfortunately you don't have any GUI for configuring that, but _after_ finding out, it's dead easy.

1. install wpa_supplicant if you don't have it already
2. edit /etc/network/interfaces and change all ra0 configs to:
> auto ra0

iface ra0 inet dhcp
pre-up iwconfig ra0  essid FOOBAR
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set Channel=N
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK=YourKey
pre-up iwpriv ra0 set TxRate=0


Where you'll replace
a) FOOBAR with your ESSID
b) N with the channel number
c) YourKey with your key

Ok, this is supposing you have dhcp, if you use a static IP address just use (instead of "iface ra0 inet dhcp"):
> 
iface ra0 inet static
address IP_ADDRESS
netmask NET_MASK
gateway GATEWAY_IP


3. ifup ra0

---

### Post by bleachlizard on 2006-08-08
Unfortunately I found out that my college doesn't really support Linux with their wireless yet.  Also, in regards to what you put up, I have installed WPA Supplicant and I've edited ../interfaces so many times I can't count it on one hand anymore.  I suppose I'm at a loss and I'll keep Windows on my laptop and put breezy on my future desktop with wired internet.  I thought it might have been something I was doing wrong, but apparently not since I've tried every suggestion across the net.  It's probably just my college's fault.  That's what I'll do, I'll blame it on my college ;) 

Thanks for the help.  If anyone has any more suggestions let me know.

---

### Post by bionnaki on 2006-08-09
I have the same card and have been successful in getting it to work. very easy - no need for wpa supplicant and all that. I can post exactly how to...when I have the time. give me a few hours. gotta get to work.

---

### Post by [Rui] on 2006-08-11
> **bleachlizard said:**
> Unfortunately I found out that my college doesn't really support Linux with their wireless yet.

That is totally irrelevant, and forgive my misdirection, but you don't really need wpasupplicant for WPA PSK and TKIP. You might need wpa_supplicant for 802.1x authentication, but that should be irrelevant from the "which OS are you using" matter.

What I think happens is that some wpa supplicant features don't work with the current version of the rt2500 driver, which needs to be upgraded as soon as the new driver reaches some level of acceptable stability.

---

