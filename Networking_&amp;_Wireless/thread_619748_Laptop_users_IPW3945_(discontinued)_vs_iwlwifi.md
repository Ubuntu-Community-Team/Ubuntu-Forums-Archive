---
title: "Laptop users IPW3945 (discontinued) vs iwlwifi"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Sygen on 2007-11-21
Sup,

I've been having problems with my Intel 3945ABG internal card using the IPW3945 driver. I looked up where to dl the latest version, and the site [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) said that they are no longer working on it, and that [http://intellinuxwireless.org/](http://intellinuxwireless.org/) is now going to be the main driver. 

Will ubuntu be going to these drivers?

For those of you that use or tested this driver, what are your thoughts on it? Better or worse?

---------------------------------------------------------
My issue with wireless
ubuntu 7.10   
--Network manager uninstalled (Wouldnt connect or read AP 80% of the time)
--Installed Wicd (Works great)
--Need to be ~20 feet closer to AP in ubuntu vs xp
--IPv6 Disabled
--On an unsecured network
--Main issue --It connects fine but disconnects, kind of. Its still shows connected but no traffic is going through. Does it randomly every 30 secs to 2 mins. EXAMPLES: Boot ubuntu -> Wicd connects -> I load Pidgin -> start chatting -> after a little bit they stop chatting and they dont receive mine. I click to view Info on them and it just says Please Wait...(its trying to get info but can't). I exit Pidgin -> reload ->(clicking offline-back to online doen't work) it works fine for the 30secs to 2mins. Same with IRC. I will be chatting, then it looks like no one is saying anything for awhile, then I get a msg, connection lost then reconnecting. Not just chat utilities either, does it with video, like youtube. Click video to view -> watch progress bar move -> randomly just stops. Sometimes it will finish, other times it will stop somewhere in between. 

It has this issue weather im 50 ft away or 5 ft away. The signal bar doesn't drop when the issue occurs. I'm a linuix newbie and would really like to eventually make it my main OS.

Hope someone can help. Thanks.
Sager laptop
Nvidia GforceGo7950GGTX
Intel Core 2 Duo T7200 2Ghz
2GB Ram
90GB HD

---

### Post by wirechief on 2007-12-12
My thinkpad R61e was having frequent errors and drops, it would disconnect after a period of time usually
after I closed the lid and woke it up the next morning I would find that it was disconnected, I would have to 
re-boot in order to get reconnected. I was using the ipw3945 and by doing this

 echo blacklist ipw3945 > /etc/modprobe.d/custom-blacklist
[ echo iwl3945 >> /etc/modules
[ then reboot
then checked to see what was loaded with 
lsmod |grep iwl
iwl3945               169448  0
mac80211              164244  1 iwl3945

so now things are working much better, and connection is much faster.
Link Quality=88/100  Signal level=-45 dBm  Noise level=-75 dBm

---

