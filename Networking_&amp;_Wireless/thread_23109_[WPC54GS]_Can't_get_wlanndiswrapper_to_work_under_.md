---
title: "[WPC54GS] Can't get wlan/ndiswrapper to work under Hoary"
date: 2005-03-31
forum: Networking &amp; Wireless
---

### Post by hda on 2005-03-31
Hi,

though it works perfectly when I boot from Knoppix 3.8 my Linksys WPC54GS refuses to work with ndiswrapper under Hoary.

Steps i tried so far:

.) installed ndiswrapper-utils and ndiswrapper-source
.) built ndiswrapper module using modules-assistant
.) inserted the windows driver using ndiswrapper -i and -m

After rebooting iwconfig shows:

```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I tried to setup the network params using both, the iwconfig and the network-admin GUI tools without success.

As I mentioned before the same configuration works under Knoppix 3.8 and Windows 2000.

Any help would be greatly appreciated.

p.s.: also, there's another problem when shutting down the system. When shutting down the network interfaces the system 'hangs' showing the following message:
```

unregister_netdevice: waiting for wlan0 to become free. Usage count = 1.

```

thanks,
hda

---

### Post by vrajmohan on 2005-04-13
I have the same problem when I shut down:
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1.

I have a NetGear MA 111 USB wireless card. I had no problems with 4.10(Warty). This started happening only when I upgraded to 5.04(Hoary).

The card works fine otherwise. I am forced to turn off my PC before it fully powers down.

I switched to using ndiswrapper and the problem went away.

--Vraj Mohan

---

### Post by kerinin on 2005-06-20
my system's doing the same thing, with the same (WPC54GS) card - when shutting down it says

```
unregister_netdevice: waiting for wlan0 to become free.  usage count = 1
``` 

over and over and over again until i pull the plug.  i'm on a dell Inspiron 7000 laptop.  i also installed ndiswrapper from source.

---

