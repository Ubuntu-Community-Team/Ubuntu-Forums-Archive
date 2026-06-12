---
title: "[SOLVED] Wireless Issue in Gutsy Gibbon (RaLink?)"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by AdHavoc on 2008-03-13
I recently installed Ubuntu 7.10 Gutsy Gibbon on my desktop PC with an Airlink101 MIMO XR 802.11g PCI adapter.  It recognizes the card but does not connect to my [unencrypted] SSID.  It lists my network in the drop down list, however.

Here is my output of "lspci -v"

```


02:09.0 Network Controller: RaLink RT2600 802.11 MIMO
                                                          Subsystem: Unknown device 17f9:0016
                                                          Flags: bus master, slow devsel, latency 64, IRQ18
                                                          Memory at felf8000 (32-bit, nonprefetchable) [size=32k]
                                                          Capabilities: <access denied>


```

I'd really like to get this working, as a computer without an internet connection is about useless for me D:

---

### Post by rustybronco on 2008-03-13
just so you know, there is hope...

this in the linksys pcmcia card I am using at this moment.
> 02:00.0 Network controller: RaLink RT2600 802.11 MIMO
	Subsystem: Linksys Unknown device 0052
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at 24000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

let me try to help.
would you post the output of 
**lshw -C network **
**iwlist scan**
**ifconfig**
**lsmod | grep rt**

****edit***ndiswrapper how-to on rt cards, which the more problems I see with ralink cards I think is the preferred way to have a stable, fast (54mbs) setup. (card can be flaky at times)
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) /end of edit

i'm using hardy, but this is the card with the rt2600 chipset in it. [http://ubuntuhcl.org/browse/product?id=258](http://ubuntuhcl.org/browse/product?id=258)
you may want to try wicd and use it to configure your wireless networks it was a lot more stable for me. [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

some reading material for you on connecting from the command line without the network manager [http://ubuntuforums.org/showthread.php?t=571188&highlight=networking+restart](http://ubuntuforums.org/showthread.php?t=571188&highlight=networking+restart)

you may want to upgrade to the hardy kernel as a last resort. (I did it on 7.10)
how-to [http://ubuntuforums.org/showthread.php?t=646755&highlight=hardy+kernel](http://ubuntuforums.org/showthread.php?t=646755&highlight=hardy+kernel)

---

### Post by AdHavoc on 2008-03-13
> **rustybronco said:**
> just so you know, there is hope...


There is hope indeed!  I actually followed wieman01's guide [here]("http://ubuntuforums.org/showthread.php?t=564419") and got everything fixed perfectly!  Thanks for your help, though :p

EDIT: Fixed title of thread

---

### Post by rustybronco on 2008-03-13
Yes, a wise choice to do it that way.
glad it's working!

back in goes my atheros chipset card....

---

### Post by Eiríkr on 2008-03-13
I noticed you added "*FIXED*" to your subject line, but unfortunately this doesn't show up in the forum message listing.  If this problem has been resolved for you, please remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

