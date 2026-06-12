---
title: "Linksys WMP11 v2.7 with ndiswrapper"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by untree on 2005-06-11
I am completely new to Linux, but I have tried to read a bit and prepare myself for it.  I had been putting off switching from windows because I'd read that my wireless card isn't supported. Then I read reports of people getting this card to work using ndiswrapper, so I decided to give it a try.  Followed these directions:
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)
but used the WMP11V27.inf file that was created by the .exe that I downloaded from the Linksys website.  I then followed both of the following to try to get it to work:
[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)
[http://www.ubuntulinux.org/wiki/WiFiTroubleshooting](http://www.ubuntulinux.org/wiki/WiFiTroubleshooting)

wlan0 shows up just fine when I type ifconfig.  It detects the hardware.  Everything seems like it should be working.  But when I try to ping anything it fails, including the wireless router.  I spent about 45 minutes fiddling around with it, but nothing seemed to help, and I meekly retreated to windows so I could ask for assistance. Can someone please tell me any specific logs or detailed information I should post to get help?  I hate to feel so helpless since I'm the guy that everyone calls when their computer stops working... but now I realize I just know my way around windows, not the computer itself.

---

### Post by kiddo on 2005-06-11
I'm pretty sure you're having the same problem as I had with my WPC11, that means a sucky linksys driver. What you have to know is that behind linksys, dlink, etc, is all the same chipset, a realtek chipset. Try to google if you can get to know what's "inside" your card maybe? You can give a try to what I used, the thingy8180.inf (realtek 81something?). Don't know if this might work for you. I don't remember if ndiswrapper said the driver was wrong or not in my case.

[http://public.nanokron.info/downloads/drivers/driver%20linksys%20WPC11v4%20(driver%20realtek%20NET8180).INF]("http://public.nanokron.info/downloads/drivers/driver%20linksys%20WPC11v4%20%28driver%20realtek%20NET8180%29.INF")

I've been fiddling with mine ~a day before getting it to work (stupid error of trusting the linksys .inf files :)), but at least I had a 10/100 pcmcia card, so that was a secondary goal (I wasn't expecting wireless to work at all someday due to my lack of knowledge)

---

### Post by untree on 2005-06-11
Thanks for your comments, but mine is a Broadcom 4301 chipset, not realtek.  I have found where people used ndiswrapper with this chipset, but they used a driver with a different name (bcm something).  I can't find it anywhere, though.  Does anyone have a .inf file that they have used for any device that uses this chipset?  also, as I said, ndiswrapper thinks mine works fine.

edit: from [this list](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List), someone claimed to get ndiswrapper to work with their BCM4301 chipset by using **bcmwl5.inf**, but I can't find a link to that file anywhere.

---

### Post by untree on 2005-06-12
SUCCESS! I am now typing this from within ubuntu!  I recompiled ndiswrapper (1.1), and used a driver I downloaded from some other site (sorry, didn't write it down & that was from windows), but it was the real deal (bcmwl5.inf).  Just thought I'd confirm that I got it working in case anyone else has the same problem.

---

