---
title: "WiFi unable to connect after wake up"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by mirko8 on 2015-04-13
Hello,
when I put my laptop( Acer Aspire E1-521) to sleep and wake it  up(no matter how much time it was in sleep) WiFi cannot connect anymore, it  just says connecting and it asks me for a password 5 times  with a delay about 20-30 seconds, before sleep WiFI was working great
Tried Ubuntu 15 beta,14, Mint and all have the same problem

sometimes the connection suceeds but I have huge ping values 1000 and increasing by 2000(not sure, will test that):

I get the same result by removing the WiFi driver and inserting it again

```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```

I think there may be a connection between the two issues, sleep & driver-restart, but I'm not an expert

do I need to run some kind of configuration after the driver has been re-inserted? or maybe restart another application/service

after hibernating or restarting my PC WiFi works again

PC: Acer Aspire E1-521
WiFi: Qualcomm Atheros AR9485 on linux, Qualcomm Atheros AR5B125 on atheros.cz

I didn't find any linux drivers on their site, all are windows

Is there a fix or at least a workaround?

Thanks

---

### Post by mirko8 on 2015-04-23
I tried the new Ubuntu 15 beta live and the problem is still there
however  I did some testing when wifi was working again and found out that by removing the ath9k,  ath9k_common, ath9k_hw, ath, mac80211 modules and inserting them wifi  worked
BUT when I removed them and the cfg80211 module, the same  problem occurs, so I'm thinking maybe the cfg80211 module needs  reconfiguring after it's been inserted again, what do you think?
Is cfg80211 removed when PC goes to sleep?

I was removing the modules one by one with ```
rmmod name
```
 but inserting with ```
modprobe -v ath9k
```

---

### Post by Ilia_Shakitko on 2015-07-02
Have you tried [that solution]("http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html") (but for your network interface)?

---

