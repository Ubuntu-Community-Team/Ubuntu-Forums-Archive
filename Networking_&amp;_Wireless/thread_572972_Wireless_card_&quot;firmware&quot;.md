---
title: "Wireless card &quot;firmware&quot;"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by gubemton on 2007-10-11
Ubuntu 7.10

The restricted driver manager is showing a firmware entry for my bcm43xx wireless card. This isn't going to actually change the wireless card's firmware, is it? Nothing wrong with the firmware, at least it works 100% in XP and Vista.

---

### Post by kevdog on 2007-10-11
You need to download the user space utilities.  The firmware is only part of the solution.  Id recommend ndiswrapper anyway for your solution

---

### Post by tturrisi on 2007-10-11
> **gubemton said:**
> Ubuntu 7.10

The restricted driver manager is showing a firmware entry for my bcm43xx wireless card. This isn't going to actually change the wireless card's firmware, is it? Nothing wrong with the firmware, at least it works 100% in XP and Vista.

No, the firmware is needed to operate the device.  The device won't get "flashed", it can't, because the device has no onboard firmware.  it will still work in Windoes.

Ignore the above re ndiswrapper.  The native bcm43xx driver + right firmware works just fine in linux.  Any issues w/ a broadcom 43xx card in linux are NOT driver issues but are issues caused by the specific linux distribution, e.g. ubiuntu & other distros sometimes incorrectly blacklist certain drivers or some network connection managers (network-manager) use screwy workarounds in order to work.

I never had any issues at all using bcm43xx drivers & firmware in Debian.

---

### Post by kevdog on 2007-10-11
Yea but whats your maximum speed using your bcm43xx driver?? -- Let's lay all your cards all the table:)

---

### Post by gubemton on 2007-10-11
The Restricted Drivers is only 1/3 of the story. It only tells you that you need some firmware thing. Another 1/3 is the USER has specify where/what firmware. And you say that user space utilities are needed.

So if I replaced XP with Ubuntu on my dad's laptop, is he going to be able to figure all this out on his own?

---

### Post by kevdog on 2007-10-11
Probably not -- you will have to do it for him.  The first time I set up the bcm43xx cutter drivers I had to do extensive searching of the forums for a how-to.  Once I found them, it was actually very easy.  Ive since gone on to ndiswrapper and thats actually easy too, however for a beginner, it is quite difficult, particularly if you have never used linux coming over from windows.

---

### Post by tturrisi on 2007-10-11
> **kevdog said:**
> Yea but whats your maximum speed using your bcm43xx driver?? -- Let's lay all your cards all the table:)
I get full capability out of the cards when I use them.  And why is this all that important anyway?  Certainly not for WWW useage.  Possibly has merit if transfer large files across a lan, but heck, I'd use the wired nic for that or a usb thumb drive or dvd.  Hell, 80211b (11 mb/s) is twice the speed of the average home broadband connection.

---

### Post by kevdog on 2007-10-11
11 Mb/sec is theoretical -- its probably like 3-4 Mb/sec actual depending on actual use (I have to confirm these numbers but have read it somewhere in the past).

54 Mb/sec - suffers a similar degree of degredation but since its starting out higher, the actual bandwidth is much higher.

As far as cds, usb drives ??? -- what about torrents, large file transfers, video downloads, etc.  

Im not starting a flame war here, but based on what you are telling me, there isnt any real reason to opt for the native driver -- except (and this is a big maybe) ease of installation (oh and Ill give you packet injection, air cracking).   When a 54 Mb/sec bcm43xx driver is released (yes I know they are working on this) Ill reconsider switching back.  But until then --- why??

---

### Post by tturrisi on 2007-10-12
> **kevdog said:**
> 11 Mb/sec is theoretical -- its probably like 3-4 Mb/sec actual depending on actual use (I have to confirm these numbers but have read it somewhere in the past).

54 Mb/sec - suffers a similar degree of degredation but since its starting out higher, the actual bandwidth is much higher.

As far as cds, usb drives ??? -- what about torrents, large file transfers, video downloads, etc.  

Im not starting a flame war here, but based on what you are telling me, there isnt any real reason to opt for the native driver -- except (and this is a big maybe) ease of installation (oh and Ill give you packet injection, air cracking).   When a 54 Mb/sec bcm43xx driver is released (yes I know they are working on this) Ill reconsider switching back.  But until then --- why??
Yes, no wars please!

Injection and monitor mode are good reasons.  As for large WWW transfers such as torrents, etc., it still doesn't matter because the "speed" of the wifi connection to the AP is still way over the bandwidth limit set by isps and servers.

For example, if use the fastest and best possible torrent seeds, you still cannot download or upload faster than the isp cap on bandwidth, there's absolutely no way to get around that, unless of course one uncaps their modem.

Most of the time if one cannot get the full 11 mb/s out of a 43xx chipset then the incorrect firmware is being used.

While ndiswrapper will enable 80211g in the device, the downside is that ndiswrapper is often buggy, and things tend to break in the ndiswrapper update-fix package cycle.

Now, to be completely honest, I ordered my Dell Lattitude D830 wi/ the Dell 1390 wifi (43xx chipset) because it was the cheapest one available.  I then replaced the mini-pci-e card with an atheros card!   The speed difference is not noticable, I used the 1390 w/ ndiswrapper and bcm43xx, and the atheros speed diff is not noticable either, but I dig atheros chipsets because they play better with kismet & aircrack-ng.

I have other broadcom cards I have used too, same results.

---

### Post by kevdog on 2007-10-12
Well one thing that I agree with you on is that the one atheros card I used is pretty awesome and worked out of the box via the madwifi restricted drivers.  I really dont notice an increase in speed, but its nice not to mess with any drivers at least one time in your life!!

---

### Post by tturrisi on 2007-10-12
Yeah man, the atheros cards are good.  The only downside is that madwifi driver does not correctly calculate the true signal levels.  Sometimes it shows as 80% even when I'm 6' from the ap.  I have 3 atheros cards and they all work well.

---

### Post by kevdog on 2007-10-12
Thanks for that piece of info on the Atheros card, I didnt know that.

Im wondering however about the whole network signal thing anyway.  I have a computer running Vista (yea I know nothing to do with ubuntu), but 1 foot away from the router its 100%, but 3 feet from the router its 80% and 5 feet from the router its 60% and 20 feet from the router its still about 58%.  I cant image 20% fall off in the initial 3 feet of the signal ... but what do I know.

So I dont know if this is specific to just Atheros cards.

---

### Post by tturrisi on 2007-10-13
Windows and linux calculate signal level and snr differently.  This calulation is based on the driver itself.  The chipset has built in capabilities and it's up to the driver to utilize those capabilities.  Windows drivers don't read or utilize certain chipset functions while linux drivers do, but not all linux drivers.  Signal level reporting is done via the driver.  The basic chipset features available via wireless=tools or madwifi tools are:
Link Quality
Signal Level
Noise Level

I don't believe windows drivers are capable of monitoring all of the above, and also madwifi has tools whereby one can set transmission levels, country codes and other things, whereas windows has no commandline tools to do these things with atheros chipsets.

One cool thing about atheros chipsets is that they can use almost any transmission level while other chipsets adhere to FCC "recommended" designs of built in limited transmission levels.  In short, you could fry eggs with an atheros chipset if so desired!

---

### Post by kevdog on 2007-10-13
router+dd-wrt (transmission power boosted) + atheros card (transmission power boosted) = one kickass wireless network!

---

