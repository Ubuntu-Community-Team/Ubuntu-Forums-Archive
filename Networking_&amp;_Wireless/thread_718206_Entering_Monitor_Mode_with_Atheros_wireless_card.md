---
title: "Entering Monitor Mode with Atheros wireless card"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by taiji_jian on 2008-03-07
Hi All,

I have a problem that seems to be frequent in incarnation, but that doesn't seem to have an integrated solution anywhere. So I am making a post to plea for help!

I am running Ubuntu Gutsy on an IBM Thinkpad t42p with an Atheros AR5212 chipset wireless card. 

I would like to be able to use aircrack-ng to crack my WEP key. 

I followed the instructions from various forum threads for putting my wireless card into monitor mode::

sudo wlanconfig ath0 destroy
sudo wlanconfig create ath wlandev wifi0 wlanmode monitor
sudo ath<X> up

This appears to work; ath<X> shows up in the output of "ifconfig" and so on. However when I start up airodump, it doesn't see any wireless networks, and ath0 doesn't record any traffic. 

Can anyone duplicate this, or explain this behavior?

---

### Post by Paris Heng on 2008-03-07
> **taiji_jian said:**
> Hi All,

I have a problem that seems to be frequent in incarnation, but that doesn't seem to have an integrated solution anywhere. So I am making a post to plea for help!

I am running Ubuntu Gutsy on an IBM Thinkpad t42p with an Atheros AR5212 chipset wireless card. 

I would like to be able to use aircrack-ng to crack my WEP key. 

I followed the instructions from various forum threads for putting my wireless card into monitor mode::

[COLOR="Red"]Line 1:[/COLOR] sudo wlanconfig ath0 destroy
[COLOR="Red"]Line 2: [/COLOR]sudo wlanconfig create **[COLOR="Red"]ath[/COLOR]** wlandev wifi0 wlanmode monitor
[COLOR="Red"]Line 3:[/COLOR] sudo ath<X> up

This appears to work; ath<X> shows up in the output of "ifconfig" and so on. However when I start up airodump, it doesn't see any wireless networks, and ath0 doesn't record any traffic. 

Can anyone duplicate this, or explain this behavior?

Did you type wrongly for the ath0 in the Line 2?

---

### Post by taiji_jian on 2008-03-08
Hi, thanks for reading.

If you type "ath" without a number, the kernel will assign the interface the next available number. Wlanconfig does create the interface successfully - it shows up in ifconfig and iwconfig - but there is no traffic on it. Scanning doesn't see any wireless networks, and the packet statistics stay at zero.

---

### Post by taiji_jian on 2008-03-08
AHA! I have solved it! 

I understood from various docs and forum posts that Atheros chipset wifi cards don't need a driver patch to enter monitor mode. A closer look at the madwifi website reveals that they do after all! I recompiled the Atheros module with sources from the madwifi site and it now works.

---

