---
title: "LAN and WLAN work, but no Inet."
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by timopekkafr on 2008-01-28
Hi,

I have a familiar problem, that I haven't found a suitable solution yet, or I've been looking in the wrong places.

I get Internet via an HSDPA modem, to my Apple laptop. From here I share it onwards, on a crosswired cable and AirPort (Wlan). My PC (Ubuntu 7.10, PCI wlan and integrated (An7) ethernet) does see both connections and connects to the laptop via FTP and SSH. However it refuses to connect to the Internet. So, the PC connects to the laptop and tarsfers files vica-versa (needless to say, ping works just fine), but doesn't see it's Net connection.

I have fooled around with DHCP, static IPs, Proxy configs, and all sorts of other stuff, with no luck.

Feeling sorrow and down, my last hope before going back to XP is this community....please... any advice?
I also tried to install my modem on my PC, but failed to get the connection working.

---

### Post by kevdog on 2008-01-28
Do you have the gateway parameter configured correctly?

route -n

---

### Post by timopekkafr on 2008-01-28
Hmmm.... yes, the gateway setting seem to be the problem.
The Apple IP is 192.168.0.1, Ubuntu is 192.168.0.2.  I fill the gateway to be the Macs IP, and still for some reason "route -n":

Destination    Gateway  Genmask            etc.
192.168.0.0     0.0.0.0   255.255.255.0

I keep on fighting....

Anyway, thank you for the tip, it gives me the source for the problem.

---

### Post by timopekkafr on 2008-01-28
I don't get it.... On the laptop I give the IP to be 192.168.0.1, on the Desktop PC I make it 0.2 and gateway to be the laptops address. For some reason however when I type "route -n" I get the destination to be 0.0 and gateway 0.0.0.0... thank God the Genmask (Subnet mask) is correct.

I am confused.

---

