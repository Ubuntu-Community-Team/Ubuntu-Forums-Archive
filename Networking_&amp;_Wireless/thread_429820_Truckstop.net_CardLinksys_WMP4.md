---
title: "Truckstop.net Card/Linksys WMP4"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by steevols on 2007-05-01
I currently own a Truckstop.net wificard [http://cgi.ebay.com/WARP-SPEED-WIRELESS-NOTEBOOK-INTERNET-CARD-ADAPTER-WiFi_W0QQitemZ150118028161QQihZ005QQcategoryZ74954QQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/WARP-SPEED-WIRELESS-NOTEBOOK-INTERNET-CARD-ADAPTER-WiFi_W0QQitemZ150118028161QQihZ005QQcategoryZ74954QQrdZ1QQcmdZViewItem")
that I bought on eBay.

When I first plugged it in Feisty Fawn, nothing happened, so I did "lspci -n" on the CLI and noticed that it labeled it as a "Linksys, A Division of Cisco Systems: Unknown device 2120".

After installing the drivers (from WinXP) with ndiswrapper, the GNOME Networking system-tray applet showed that I had a wireless card, but it doesn't SEEM to be working. When I tried all this in Slack 11, it would show networks, but refused to let me join.

Any suggestions? Does it work on older versions of Ubuntu?

The card is labeled (physically) as a C130 "GetOn" Truckstop.net.

---

### Post by chili555 on 2007-05-01
What does ```
ndiswrapper -l
```tell us?

Does this help:> Card: PCMCIA card INPROCOMM IPN2120 distributed by truckstop.net
    * Chipset: INPROCOMM
    * pciid: 17fe:2120
    * Driver: ndis 1.1-4 w packaged WinXP driver and kernel 2.6.11 on Debian unstable
    * Other: Truckstop.net is currently in litigation so the cards can be had for $10. The driver can be had from [154]. lspci reports: Ethernet controller: Linksys, A Division of Cisco Systems: Unknown device 2120. I originally spotted this one on a support list for ndis under the Linksys brand.
    * Other:Works great with the linksys driver found here: [ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip](ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip), with the LSIPNDS.inf file. This is from [http://ndiswrapper.sourceforge.net/joomla/?title=List](http://ndiswrapper.sourceforge.net/joomla/?title=List)

---

### Post by steevols on 2007-05-02
Thanks so much! I'll try that driver now. BTW, ndis... -l gives the all clear.

---

