---
title: "Ralink wireless problem half solved"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by pea-brane on 2008-03-16
Like many others, I have been suffering from the problems with the problems with getting ralink wireless hardware to work with Xubuntu. I seem to have stumbled across half a solution which I have not seen published elsewhere. First, the tediously long path to where I am today...

I was running 7.04 until my ADSL modem/router forgot it was supposed to connect to the internet. So I bought a new one. I could not get my wifi card (Edimax EW-7108PCg - an RT2500) to work with the new box. So I thought it was about time to upgrade to Xununtu 7.10 (from Farting Filly to Gusty Gorilla - of whatever cringe-worthy alliterations they use). This was a disaster. Apart from being the buggiest release of Linux I have seen in about 8 years, the Line and Tx lights on the wifi card were now permanently on. (Having been rude about Xubuntu, I do like the installed product - I would not have spent so much time on it if I thought otherwise).

I "rtfm"ed and Googled everything I could find, I even tried 8.04 Alpha 6 (Humping Hampster?) which was at the stage of running a bum update which killed the system - so I reloaded 7.10. I also purchased a different wifi card (a D-Link DWL-G630) under the incorrect impression that it contained a non ralink chipset. At least the Line and Tx lights looked half-way sensible on that. At various times I tried loading Windows XP and serialmonkey drivers without luck. (Serialmonkey sees Serialmonkey does?).

Everything looked like it should work,it just didn't. I persevered with pratting about attempting to find a solution and randomly found a set of commands which caused the card to burst into operation. Remembering that I have discarded my Rt2500 (wlan0) and replaced it with an Rt61 (wlan1), I typed (as root) ...

ifdown eth0
ifdown wlan1
ifup wlan1
ifup eth0

Note that the ifdown wlan1 gives the response...

RTNETLINK answers: No such process
... whatever that means.

For some reason, the above set of commands only work if I boot with the modem router switched on and not if I switch it on later.

I attempted to put some pre-up and post-up commands into /etc/network/interfaces to mimic this but all attempts resulted in the RT61 card lights flashing dementedly and the system going so slow that it hardly ran (I have an ancient HP Omnibook 6000).

For the record, I am using static IP addresses with an open hex 64 bit/10 digit WEP code.

While I can just about grasp what these ifconfig and iwconfig commands are doing, I am now well out of my depth. Besides, this solution may help others (as so many others have helped me over the years). I also think I am trying to treat the symptoms and not the cause.

So in conclusion, I'm wondering if anyone can please suggest an "automatic" solution to this or at least where to go next. And should I be reporting my findings as an Xubuntu bug?

I have listed the verbose output from the ifdown/ifup commands (not that I think it helps much). Perhaps I should have listed a whole load of other files as well but I think this post is too long already.

root@cougar:~# ifdown -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
 route del default gw 192.168.0.1 metric 100 eth0 
ifconfig eth0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant

root@cougar:~# ifdown -v wlan1
Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
RTNETLINK answers: No such process
run-parts: executing /etc/network/if-down.d/wpasupplicant
 route del default gw 192.168.0.1 metric 100 wlan1 
ifconfig wlan1 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant

root@cougar:~# ifup -v wlan1
Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig wlan1 192.168.0.10 netmask 255.255.255.0               up
 route add default gw 192.168.0.1 metric 100 wlan1 
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

root@cougar:~# ifup -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig eth0 192.168.0.6 netmask 255.255.255.0                 up
 route add default gw 192.168.0.1 metric 100 eth0 
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant


Any thoughts or ideas, greatly appreciated.

---

### Post by pea-brane on 2008-03-22
I guess few if any people are having this problem as there have been no replies to this in over a week.

Some further information: I should have noticed when I changed from the rt2500 to the rt61 wifi card that there was something in dmesg that was not there before. I thought it was the same problem. Looks like it was not.

The relevant bit from dmesg is...

[   40.800000] ieee80211_init: failed to initialize WME (err=-17)
[   40.812000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_con
trol_unregister
[   40.812000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   40.816000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   40.816000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_con
trol_register
[   40.816000] wmaster0: Selected rate control algorithm 'simple'
[   41.240000] ADDRCONF(NETDEV_UP): wlan1: link is not ready

I don't know what this means and googling the problem, it seems that one or two others have the similar (but not the same) issue. I have not seen any likely solutions elsewhere.

I can still solve my problem with the combination of ifdown and ifup as I outlined in my previous post. I've now added these commands to rc.local so my rt61 comes up OK. So I don't see any point in chasing this one down any further.

---

