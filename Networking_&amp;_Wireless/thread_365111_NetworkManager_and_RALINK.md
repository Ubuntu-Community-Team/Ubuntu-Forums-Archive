---
title: "NetworkManager and RALINK"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by ctsdownloads on 2007-02-19
I have been trying and trying to determine one, just one manufacturer that produced a wireless card that **openly supported** Linux (no ndiswrapper nonsense, thanks). After no less than six full months of exhaustive searching I have found one. Edimax and their [_EW-7608Pg_]("http://www.edimax.com.tw/html/english/products/EW-7608Pg.htm") PCMCIA card. Great, just one issue - it's based on RALINK.

Now RALINK is supported in Linux by default, but for some reason no RALINK cards ever show up in [network-manager-gnome]("http://www.gnome.org/projects/NetworkManager/"); what's up with that?

Is it just my notebook? This makes network selection a real pain as [_wifi-radar_]("http://wifi-radar.systemimager.org/") has never been able to detect anything on my notebook whatsoever.

----

Ubuntu:
Edgy

Hardware:

Notebook- 
Averatec 3200

wifi cards- 
Zonet ZEW1501 (works on home network, but not seen with network-manager-gnome)
Gigafast WF728-AEX ((works on home network and is seen with network-manager-gnome)

---

### Post by erkki70 on 2007-02-19
Hi,
I use a DWL g 630 rev. E D-Link card with the RT61 Ralink driver and it looks like it's a known issue that Network-Manager doesn't recognize the card.
there's a project called ra0dar on SourceForge but I didn't try it.
Alternatively, there's a script in this thread:
[http://www.ubuntuforums.org/showpost.php?p=1910477&postcount=116](http://www.ubuntuforums.org/showpost.php?p=1910477&postcount=116)

I've to say I do agree, it's still a pain to get flexibility for choosing appropriate Wireless Network...

Hope this helps.

Cheers,

---

### Post by ctsdownloads on 2007-02-19
Thanks.

Lucky for me, it connects (at home) so for outside the home with networkmanager, I will use my Gigafast card. 

My reason for being frustrated with network-manager's lack of Ralink support is that had it worked with network-manager, I could find myself with a stronger argument in working directly with Edimax to maintain their usage of the Ralink driver in the future. Any idea why the hell we have such an obvious GNOME bug with a chipset that has been so good to Linux with its support? Frankly, this seems rather stupid to me as Ra0 has been good to use otherwise. :confused:

---

