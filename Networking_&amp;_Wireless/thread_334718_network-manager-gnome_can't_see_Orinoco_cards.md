---
title: "network-manager-gnome can't see Orinoco cards?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by @trophy on 2007-01-09
I got my wireless card (2Wire branded Orinoco Gold) working (with the stock drivers that are already in the kernel) as far as accessing an AP goes, but network-manager-gnome still can only see the wired network.  I think this might have something to do with the drivers,  because when I use ndiswrapper with my other (Belkin) card nm-applet can see the wireless networks just fine.

Can someone else who uses an Orinoco confirm this?  Can your network manager see the wireless networks, or not?

---

### Post by @trophy on 2007-01-10
NOBODY else on these forums has an Orinoco Gold card?!  Why do I find that hard to believe?

Come on guys, I just need to know if anybody's gotten this working yet, and both google and these forums have turned up nothing.

---

### Post by riven0 on 2007-01-10
To be honest, I've never heard of the Orinoco card. But have you tried **iwconfig** yet? What output does it give you?

---

### Post by @trophy on 2007-01-10
> **riven0 said:**
> To be honest, I've never heard of the Orinoco card. But have you tried **iwconfig** yet? What output does it give you?

Well hey first off, thanks for the reply.  I really appreciate it.  It's good to know someone at least actually read my post!  :)   Anyways, the problems I'm having are explained in the following two threads.  (the first thread will say that the problem has been solved, but it has since returned)

[http://ubuntuforums.org/showthread.php?t=333668&highlight=orinoco](http://ubuntuforums.org/showthread.php?t=333668&highlight=orinoco)
[http://ubuntuforums.org/showthread.php?t=334147](http://ubuntuforums.org/showthread.php?t=334147)


As it stands right now, I have de-patched the orinoco card by putting the old drivers back where they belong, checking /etc/network/interfaces to make sure nothing but loopback was enabled, and then rebooting.  Upon logging in again, eth1 (my orinoco card) is down by default, so first thing I do is an ifconfig eth1 up.  Lights come on... so far so good.

Network Manager still can't see the wireless networks, though.  Left click it and all you see is the wired network.  That's Problem #1, which this thread is about.  I'd like to know if this is a problem with the orinoco cards/drivers/firmware, because with my other (Belkin, Broadcom43xx) card + ndiswrapper and the windows driver Network Manager works just fine. 

But if I ignore problem #1, I immediately run into problem #2.  To do that, we drop to the command line again, and try the following:

ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:02:2D:B5:50:71  
          inet6 addr: fe80::202:2dff:feb5:5071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:269 (269.0 b)  TX bytes:792 (792.0 b)
          Interrupt:3 Base address:0x3100 

```

iwconfig eth1 (connected to an open AP around here that I use for testing sometimes... DHCP is working on that AP)
```
eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:E3:CB:1A   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=7/92  Signal level=-86 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

```

Bringing the interface down, resetting the card, and bringing it back up does nothing.

So I'm not real sure what else to try... I bought the orinoco because several linux friends told me it was the best card in existance, and I checked before I bought it to make sure it had native linux drivers... this is a sad turn of events indeed if ndiswrapper is outperforming the native drivers...  anyway if you know what else I could try, please let me know.

---

### Post by @trophy on 2007-01-11
Bump.

---

### Post by tturrisi on 2007-01-12
I too have that orinoco 2wire card.  It works just fine for me.  Bear in mind it is NOT the same as the earlier "real" orinoco cards your friens speak of, it has an agere chipset, not a prism chipset, but it's still a decent card.  It uses 2 drivers, hermes and orinoco_cs.  Do:
modprobe hermes
modprobe orinoco_cs
after booting.
Also, check the latter (bottom section) of /var/log/dmesg immediately after booting to see any errors or if those drivers attempt to load at boot.  If nothing in dmesg re orinoco_cs then verify your /etc/network/interfaces contains the following:
auto eth2
iface eth2 inet dhcp
wireless-essid YOUR-WLAN-SSID-HERE
if not there, add it and reboot.
note: where eth2 = YOUR ethX interface.

---

### Post by @trophy on 2007-01-12
> **tturrisi said:**
> I too have that orinoco 2wire card.  It works just fine for me.  Bear in mind it is NOT the same as the earlier "real" orinoco cards your friens speak of, it has an agere chipset, not a prism chipset, but it's still a decent card.  It uses 2 drivers, hermes and orinoco_cs.  Do:
modprobe hermes
modprobe orinoco_cs
after booting.
Also, check the latter (bottom section) of /var/log/dmesg immediately after booting to see any errors or if those drivers attempt to load at boot.  If nothing in dmesg re orinoco_cs then verify your /etc/network/interfaces contains the following:
auto eth2
iface eth2 inet dhcp
wireless-essid YOUR-WLAN-SSID-HERE
if not there, add it and reboot.
note: where eth2 = YOUR ethX interface.

Are you sure it's an agere chipset?  The guy who sold it to me claimed that it was a Hermes I chipset, which is I think fairly probable, considering that it uses the hermes driver.

Anyways have you tried the patched (for monitor mode) drivers?  When I use them, network manager won't work... when I use the stock drivers, network manager works, but wpasupplicant won't... so I'm curious as to whether others have had the same issues.

---

### Post by tturrisi on 2007-01-12
This is the 2wire card I have:
[http://www.pcliquidations.com/item.asp?id=1525](http://www.pcliquidations.com/item.asp?id=1525)

There have been several version of the proxim Orinoco cards over the years, some have prism chipsets, some have agere chipsets and the latest proxim orinocos have atheros chipsets.  The original lucent orinocos are 80211b only and any 80211b cards don't support WPA unless the chipset firmware gets flash updated.

I use the patched drivers w/ my 2wire and can also use wep w/ it, but not wpa.  I don't use network-manager though, I just use the net-admin applet. 

> 
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html)
Orinoco driver : One driver, 3 hardwares...
The Orinoco driver support 3 hardware which are very closely related but slightly different :

    * Lucent/Agere Orinoco Pcmcia cards and Apple Airport (howto)
    * Intersil PrismII Pcmcia/PLX/PCI cards (howto)
    * Symbol Spectrum24 HR Pcmcia cards (howto) 

If you look in the Wireless Howto, you will find that each of these hardware have other drivers available. For the Orinoco, we list those drivers in the previous section. For PrismII, there are the famous linux-wlan-ng and HostAP drivers, which have advantages over this driver.

Because Orinoco support all those hardware, people think they are the same hardware. However, all those other drivers support only one of these hardware, and only the Orinoco driver support all three of them. At boot, the Orinoco driver will print in the message logs which of the three hardware it has detected, with the firmware version number. 

To find out what chipset the card has check /var/log/dmesg

---

### Post by @trophy on 2007-01-13
Ok, I believe mine to be one of the B only cards, with the firmware updated (as I have connected to WPA with it before... not sure what's changed since then, but WPA doesn't work now).  Anyways everything I can see says it's a Hermes I chipset... so I guess it's one of the originals?

---

### Post by tturrisi on 2007-01-13
Lucent-Agere & Hermes are synonymous.  Hermes was a product of Lucent.  Lucent becaome Agere (corporate aquisitions).  Your card could be an original or a duplicate-remake-refurbished model.  The originals looked like this: (lower page)
[http://seattlewireless.net/LucentWirelessCard](http://seattlewireless.net/LucentWirelessCard)

Regardless, I am not certain that the orinoco driver supports WPA entirely.   My card works in windows & linux.  The firmware is version 7.86.38.623.  You can find what your chipset  is exactly by viewing the windows drivers for the card if you have it working in windows.  When I installed the drivers under windows it flashed the chipset to the latest version.   The latest version of the driver upgrades the card's capabilities from 64 bit WEP to 128 bit WEP, but has no support for WPA.

---

### Post by @trophy on 2007-01-13
Awesome!  Thanks for all the useful information!!!  I'm a lot closer to getting the whole thing to work now!

---

