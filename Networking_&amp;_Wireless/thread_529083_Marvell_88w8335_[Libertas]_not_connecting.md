---
title: "Marvell 88w8335 [Libertas] not connecting"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by MenZa on 2007-08-18
I've installed the Windows driver for my PCMCIA WLAN card, and it does appear to be working, in the sense that I can scan for networks, see whether/how they're secured, etc., but when I attempt to connect to one, network-manager-gnome doesn't connect; it flashes the icons like it's connecting for a few seconds before returning to its state of "Not connected".

I initially tried to install the driver with ndisgtk, but I feared that was the problem, so instead I installed the .inf and .sys file with *ndiswrapper -i*. *ndiswrapper -l* lists the driver, and notes that the device is connected:

```
mrv8335 : driver installed
	device (11AB:1FAA) present
```

So that doesn't appear to be the issue. Now, Wifi-radar automatically connects me to the nearest accessible network---in this case my unsecured Fon network---but I can't seem to load any websites Fon normally allows, even though you haven't logged in (for those that don't know, [Fon](http://fon.com) is a service to share your wifi with other Fon users, provided they login), namely Google.com and Fon.com, even though it does show it as connected in my iwconfig:

```
wlan0     IEEE 802.11g  ESSID:"FON_NETNAME"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:84:14:15:DD   
          Bit Rate=36 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any ideas what's wrong here?

---

### Post by MenZa on 2007-08-19
Right. I fell over an article on the [Ubuntu Community Wiki](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k), and I did everything as instructed; disabled the mrv8k kernel module, removed network-manager(-gnome) and installed Wicd, but I'm still having no luck connecting!

I can connect to the wired network, but I can still only see my wireless networks, but it refuses to connect to them.

---

