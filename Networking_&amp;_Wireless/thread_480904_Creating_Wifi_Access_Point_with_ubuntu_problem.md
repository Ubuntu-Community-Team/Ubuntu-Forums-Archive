---
title: "Creating Wifi Access Point with ubuntu problem"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Tomasu82 on 2007-06-21
I'm having a small issue with the wifi networking in ubuntu.

I've set it up according to the docs, and it won't set the channel on "ifup" or "invoke-rc.d networking restart". My Wifi clients (primarily my Nintendo DS) won't see the AP till I manually call iwconfig to set the channel/freq it works fine afterwards.

this is my current setup:
```
iface ath0 inet manual
        madwifi-base wifi0
        madwifi-mode Master
        post-up iwconfig ath0 essid MYESSID nick MYESSID2 freq 10
        wireless-channel 10
        wireless-freq 10
```

I've also tried without the duplication of the channel/freq settings. The interface comes up just fine, but nothing will see the AP until I manually call "iwconfig ath0 freq 10" or any channel from 4 through 11.

Since it seems to not keep my preferred channel, and defaults to channel 1, which doesn't seem to work at all with my Nintendo DS (1-3 don't work with it for some reason).

I've been playing with this for a few days now, and I can't find any info on why this is happening.

I'd really appreciate any help.

---

### Post by axels22 on 2007-12-24
I know this is probably a late reply to your post, but I thought I would still try to close it.

I was also struggling with this problem when I upgraded from 6.06 to 7.10.

It seems like the syntax has slightly changes with the upgrade.

Instead of "wireless-channel 10", insert **channel 10**

However, I didn't need to enter a frequency setting to get mine to work.

For reference, the following is the settings that I have in my /etc/network/interfaces for ath0:

auto ath0
iface ath0 inet manual
madwifi-base wifi0
madwifi-mode master
wireless_essid spreher
channel 11

---

