---
title: "ALERT: new drivers for WG111, RTL8187"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by vronp on 2006-08-17
Hi All,

I see that the accepted method to get this chipset to work seems to be using ndiswrappers.  My understanding is that this is the method of last resort.

Just curious to know if anyone has seen the various Linux drivers for this chipset (RTL8187) on:

[www.realtek.com.tw/downloads](www.realtek.com.tw/downloads)

I'm going to take a crack at it now.  

Dave

---

### Post by zoram on 2006-08-22
any luck ?

---

### Post by froh on 2006-09-06
I am using the linux drivers from realtek now, modinfo says they are version 1.1. They work ok, i have about the same performance as in windows. But wep encryption won`t work even if i have the ieee80211_crypt_wep_rtl module loaded. This might or might not be related to the driver.

For some reason ndiswrapper and the r8178 fom dapper let me see the dongle in iwcofig, but fails to scan or connect to the ap.

---

### Post by ashram on 2006-10-14
I got it working with ndiswrapper and relatek drivers win98/me...

It is working with WEP.

Sometimes it's disconnecting... hope you'll have more luck

---

### Post by Zer0Nin3r on 2007-01-07
> **froh said:**
> I am using the linux drivers from realtek now, modinfo says they are version 1.1. They work ok, i have about the same performance as in windows. But wep encryption won`t work even if i have the ieee80211_crypt_wep_rtl module loaded. This might or might not be related to the driver.

For some reason ndiswrapper and the r8178 fom dapper let me see the dongle in 'iwconfig', but fails to scan or connect to the ap.


I just installed Edgy and have been having problems connecting to the router.  I'm able to see the router just fine when doing 'iwlist', and I'll recieve packets from time to time, but I'm not getting any transmit (outbound) going on when looking at wlan0 under networking tools (gui).  When looking at the readme for the Linux drivers I'm seeing v1.1 came out earlier in 2006?  Would the version that's packaged with Edgy be better suited?  And is Ubuntu's version 1.0?

I tried to install the linux drivers, but I'm not sure I'm doing it correctly.  I'll follow in instructions that came with them, and then I'll get stuck after 'making' the driver.

---

