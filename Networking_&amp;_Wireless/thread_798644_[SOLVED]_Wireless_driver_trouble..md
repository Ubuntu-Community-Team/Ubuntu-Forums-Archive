---
title: "[SOLVED] Wireless driver trouble."
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by I am outlaw on 2008-05-18
Well, I'm a very new user of Ubuntu, I was curious if someone could help me out here. I'm trying to find and install the driver for my wireless card. I did a search and I found a post was made before about the same card but no solution. [http://www.uluga.ubuntuforums.org/showthread.php?t=738135&page=2]("http://www.uluga.ubuntuforums.org/showthread.php?t=738135&page=2")
There's the link, I exhausted all the options the people in that thread suggested. A issue maybe that I can't get ndiswrapper installed, I tried the command as suggested and also downloaded it from the site, following installation instructions, still no good. I'm running ubuntu 8.04. I'm also dual booting with Vista, I have the Vista driver, but from what I understand is that I need the XP driver for the card, correct?
Edit
I got the ndiswrapper installed, and I found a driver which is still the Vista driver it says it's installed but I cannot connect to a wireless network nor have the option too. I get no logical name and network is UNCLAIMED.

Any help would be greatly appreciated.

Thanks.

---

### Post by wdaniels on 2008-05-18
> **I am outlaw said:**
> I have the Vista driver, but from what I understand is that I need the XP driver for the card, correct?

Yes, you will need an XP driver for ndiswrapper. I don't have this card, so I can't check for you, but I found a thread [here]("http://www.fatwallet.com/forums/computers/741035/?start=20") which points to an XP driver provided by NETGEAR for this chipset.

The driver can be downloaded from [this link]("http://kbserver.netgear.com/release_notes/d103154.asp") but you may need to install wine first so that you can get at the extracted files (since the download is an EXE).

I also found some reports of success using that driver in [this thread]("http://ubuntuforums.org/archive/index.php/t-575785.html").

Hope this helps.

---

### Post by I am outlaw on 2008-05-18
Thanks man! I got it! I appreciate the help.

---

