---
title: "Installed Ralink wireless USB adapter &amp; now log filling with messages."
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by daemoncycler on 2014-03-19
Hi,

Just installed a Ralink wireless USB adapter which seems to be working OK however the syslog if full of the following messages.  Some searching indicates a possible patch but these are vague references on Linux developer forums.  Can anyone tell me what is going on?

This is a Panda Mid-Range WiFi N USB Adapter & is supposed to be plug-n-play for Ubuntu thru 13.04 & I m running Lubuntu 13.10.

Thanks

```
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.568140] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.568171] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.568175] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.568220] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.592517] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.592634] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.824344] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.824364] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.824369] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.824411] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.828846] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.828872] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.828876] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.828923] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.832214] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.832406] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.832413] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.836715] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.836736] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.836741] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.836777] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860337] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860367] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860372] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860415] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860430] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.860444] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.864836] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.864865] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.864870] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.864912] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.872709] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.872728] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.872733] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.872773] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.908709] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.908827] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.908952] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.909076] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.909202] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.949453] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.949570] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.949695] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.949819] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.949944] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.950072] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.950320] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.950449] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.950571] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
Mar 18 22:43:59 spyder-Pavilion-zd7000-DM791A-ABA kernel: [  998.976949] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
```

Edit: Upon further review these messages only come out occasionally & then for about 10 seconds each time.

---

### Post by th-heuer on 2014-08-16
Hi, I've found a work-around a little while ago which relies on using an old kernel: [http://thheuer.com/2014/05/ubuntu-14-04-asus-n13-wireless-usb-adapter-problems-howto/](http://thheuer.com/2014/05/ubuntu-14-04-asus-n13-wireless-usb-adapter-problems-howto/) .

Hope this helps.

---

