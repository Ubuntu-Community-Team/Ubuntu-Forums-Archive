---
title: "Uninstall or reset wireless driver"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-01-23
I have an Atheros AR5006EG chipset with ndiswrapper+net5211 installed as the driver. NOTHING seems to be getting my wireless card going.

Could anyone help with uninstalling or disabling my driver so I can test out madwifi for my driver? Does that plan sound reasonable??

If anyone wants any posts of terminal output to see what I'm seeing, let me know.

Thanks in advance!

---

### Post by deltaprime on 2008-01-23
sure let me see a terminal output.
to unload the driver you can type in 

**~# sudo modprobe -r xxxx**

[COLOR="darkred"]NOTE: replace xxxx with the name of your driver[/COLOR]

and then you could add your card to the blacklist so it doesnt load it when you boot up.

**~# echo "blacklist xxxx" | sudo tee /etc/modprobe.d/xxxx**

[COLOR="DarkRed"]NOTE: replace xxxx with the name of your driver[/COLOR]

---

### Post by deltaprime on 2008-01-23
Hope it works keep me up dated

DELTA

---

### Post by bwtranch on 2008-01-23
Stupid question, but did you look at the OEM's website?

---

### Post by smooveg on 2008-01-23
> **deltaprime said:**
> sure let me see a terminal output.
to unload the driver you can type in 

**~# sudo modprobe -r xxxx**

[COLOR="darkred"]NOTE: replace xxxx with the name of your driver[/COLOR]

and then you could add your card to the blacklist so it doesnt load it when you boot up.

**~# echo "blacklist xxxx" | sudo tee /etc/modprobe.d/xxxx**

[COLOR="DarkRed"]NOTE: replace xxxx with the name of your driver[/COLOR]

Funny thing -- I blacklisted the ath-*** drivers before installing the net5211 driver, now removed the blacklisting, and I get this output from iwconfig:

wlan0     IEEE 802.11g  ESSID off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Power Management off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

...and this from ndiswrapper -1:
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

Hopefully once I blacklist the net5211 and install madwifi all will be OK.

---

### Post by smooveg on 2008-01-23
Weird situation FYI:

I was not able to get my wireless card to function, even though it was a recognized device. So I:

- Blacklisted all wireless drivers
- Installed ndiswrapper with Atheros 5006EG driver (net5211)

Nothing worked.

But now, I un-blacklisted the other drivers, scanned for networks and viola -- all available networks showed up. Now I've got to deal with a KNetworkManager (using Kubuntu) that doesn't seem to want to manage my wireless connection at all. Will try Wicd or just the terminal, or suggestions??

---

