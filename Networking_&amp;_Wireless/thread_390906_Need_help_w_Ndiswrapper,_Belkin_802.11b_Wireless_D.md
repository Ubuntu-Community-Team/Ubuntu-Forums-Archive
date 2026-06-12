---
title: "Need help w/ Ndiswrapper, Belkin 802.11b Wireless Desktop Network Card (F5D6001)(PCI)"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Orange Juice on 2007-03-22
I downloaded "ubuntu-6.10-desktop-i386.iso" off of torrents and I need help using ndiswrapper.

This is what I have:

> 
Card: Belkin 802.11b Wireless Desktop Network Card (F5D6001) (PCI)

    * Chipset: RTL8180 Board: V1799 F5D6001 Rev 2.0
    * pciid: 1799:6001 (rev 20)
    * Driver: [44] (click on) ndis5x-8180(170).zip
    * Other: This PCI card works with ndiswrapper v0.10 when you use RTL8080 driver, not Belkin driver. The PCIID of this card is different from Realtek driver's supported PCIID, so you need to tell ndiswrapper to use realtek driver for 1799:6001. So execute "ndiswrapper -d 1799:6001 net8180". Now make sure ndiswrapper got it right by checking the output "ndiswrapper -l". It should print "net8180 driver present, hardware present".
    * Other: Card also works using (173).zip driver, with Ndiswrapper 1.7 on 2.6.15-rc7 and 1.8 on 2.6.15 (with 4K stacks!) on a debian box. 


[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

I'm completely new to Linux so Idk what to do. I'm going to need the exact instructions written out. I think I need ndis5x-8180(170).zip and ndiswrapper v0.10. On the Realtek site, they updated their drivers so the only version available to download is ndis5x-8180(173).zip. I haven't checked to see if I will be able to download ndiswrapper v0.10.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L)

I found the link below on another forum. The person has the exact same wireless card and the steps they took to fix it:

[http://www.computing.net/linux/wwwboard/forum/28204.html](http://www.computing.net/linux/wwwboard/forum/28204.html)

---

