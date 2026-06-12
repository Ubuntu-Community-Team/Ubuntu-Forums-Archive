---
title: "Kubuntu-friendly wireless adapters"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by barq on 2006-11-09
Hi

I'm looking for suggestions for a wireless network adapter (802.11b/g) (preferably USB, but PCI is an option) that is relatively easy to set up in kubuntu dapper.

I guess this probably means I want something which is natively supported by dapper rather than using ndiswrapper. I know many adapters come in different versions which makes this harder, but given that I'm buying specifically for a kubuntu box what suggestions would you make?

I'm pretty new to kubuntu so the simpler the solution the better :-) Also I don't have much wireless experience (I've only set up wired LANs before). If it makes any difference I'm in the UK so suggestions that are available from retailers like dabs, ebuyer, pc world are especially welcome.

Thanks for reading, all suggestions welcome.

---

### Post by esaym on 2006-11-09
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

also 3com is good: [http://www.linuxquestions.org/hcl/showcat.php/cat/122](http://www.linuxquestions.org/hcl/showcat.php/cat/122)

---

### Post by FrodoB on 2006-11-09
The Atheros chipset is one of my favorites, but madwifi does not support USB devices at all and the web site says that it is not likely to ever occur. 

To use Atheros USB devices you would have to use ndiswrapper and it only seems to work with certain devices and certain Windows drivers. I have been about 25% successful with it overall and can't recommend it.  I would only use it if I had a friend nearby who has the exact model and version of wireless device that I am buying, so they could assist me. Many folks who have been successful with it swear by it and for some devices out there it is your only choice.

As far as USB and native Linux drivers, the chipsets that I have used are the Zydas zd1211b, Ralink RT2571W and the RealTek rtl8187. 

The RealTek device happens to work out of the box with Edgy, but as far as I know it was not popular and unless you happen to have easy access to one I can not recommend it. Besides it may not work in the next version of Ubuntu and the drivers do not seem to be actively supported? 

The Belkin devices are available at most Wal-mart and Best Buy stores that I have been to in the US. They are more expensive at retail stores ($40), but most have a workable return policy, well at least Wal-mart for sure.

Here is the list of USB devices that I have used:
 
Belkin FD57050 ver 3000 - Ralink RT2571W - driver rt73 from Ralink site: [http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralink.com.tw/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

Belkin FD57050 ver 4000 - Zydas zd1211b - driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Gigafast WF748-CUI - Zydas zd1211b - driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Airlink101 AWLL3026 - Zydas zd1211b - driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Netgear WG111 v2 - rtl8187 - Seems to work immediately with Edgy, no longer in production?

The the Zydas devices seem to work well, but the Belkin version is larger and maybe the heat dissipation from the device is better than the Airlink101 and Gigafast devices? At any rate it is cooler to the touch. You have to blacklist the zd1211rw driver that is currently installed in Edgy because it does not work correctly. You have to download the kernel source to compile the driver.

The Belkin F5D7050 ver 3000 is the prior version and it seems to work better with Linux than with Windows due to the drivers. It does have to be given an "ifconfig rausb0 up" command to wakeup and work. I have been able to automate this in Edgy, but not Freespire or Slackware yet. Again you need the driver and kernel source to install it. The driver source (rtmp_def.h) has to be modified to see the device ID (0x050d,0x705a). If you have easy access to this one then I could post a howto for creating and installing the driver.

I did not even know that the Netgear WG111 v2 works with Edgy out of the box until someone asked the question last night so I put it in my Edgy box and it was seen and available for setup in a few seconds. I have only used it for an hour or so, so I cannot comment on stability.

A good site to check for Linux compatibility is Hendrik-Jan Heins' Passys site:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

You can look by manufacturer, type like USB, or chipset.

Also take a look at:

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

If you have easy access to these devices, just download and install the drivers and do not even go and purchase the cards until you have successfully installed the drivers. Or better yet maybe you could borrow the device from a friend to verify it before you purchase it. That could save a lot of frustration.

Maybe some other folks can post some devices that work right out of the box. Other than the WG111 v2 all of the devices I know of require making the drivers from source.


Good Luck,

Frodo

---

