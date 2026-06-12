---
title: "Unable to connect to wireless network with 8.04"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by sroberts82 on 2008-04-27
Hi,
I am using Ubuntu 8.04 on an Acer Travelmate 5720. I am having difficulty connecting to my wireless network with ubuntu, but on the same laptop I can connect using windows. I believe the card to be working, at least to a point because it appears to be able to communicate with the router. I think this because of the following messages in my system debug log:
```

Apr 27 20:07:36 stephen-laptop NetworkManager: <debug> [1209323256.665655] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'BTVOYAGER2091-34' 
Apr 27 20:08:00 stephen-laptop kernel: [  177.091598] wlan0: Initial auth_alg=0
Apr 27 20:08:00 stephen-laptop kernel: [  177.091609] wlan0: authenticate with AP 00:11:f5:f2:ee:34
Apr 27 20:08:00 stephen-laptop kernel: [  177.094958] wlan0: RX authentication from 00:11:f5:f2:ee:34 (alg=0 transaction=2 status=0)
Apr 27 20:08:00 stephen-laptop kernel: [  177.094966] wlan0: authenticated
Apr 27 20:08:00 stephen-laptop kernel: [  177.094971] wlan0: associate with AP 00:11:f5:f2:ee:34
Apr 27 20:08:00 stephen-laptop kernel: [  177.097221] wlan0: RX AssocResp from 00:11:f5:f2:ee:34 (capab=0x411 status=0 aid=4)
Apr 27 20:08:00 stephen-laptop kernel: [  177.097228] wlan0: associated
Apr 27 20:08:00 stephen-laptop kernel: [  177.103790] wlan0: association frame received from 00:11:f5:f2:ee:34, but not in associate state - ignored
Apr 27 20:08:02 stephen-laptop kernel: [  178.167028] wlan0: RX WEP frame, decrypt failed
Apr 27 20:08:10 stephen-laptop kernel: [  179.828392] wlan0: no IPv6 routers present
Apr 27 20:08:45 stephen-laptop NetworkManager: <debug> [1209323325.491104] real_act_stage4_ip_config_timeout(): Activation (wlan0/wireless): could not get IP configuration info for 'BTVOYAGER2091-34', asking for new key. 
```


Has anyone seen this before that might be able to help me?
Thanks,
Stephen

---

### Post by sroberts82 on 2008-04-27
bump....

---

### Post by chrisdfh on 2008-04-29
I have an Acer Aspire 5720z (5720-4126) With Atheros 5700EG Wireless card.

On the restricted drivers it shows, also shows under LSPCI, but under nm-applet, or under iwconfig it doesnt show. Any ideas to get this working???

---

### Post by sroberts82 on 2008-05-04
After some more googling I found it to be a bug (I can't actually find the link now) with the driver for the wireless card in my laptop. I have installed 7.10 and it connects fine without any work at all so I guess I'll have to wait for this to be fixed before I can upgrade. Or I could try fix it myself....hmmmmmm

---

### Post by chrisdfh on 2008-05-06
> **sroberts82 said:**
> After some more googling I found it to be a bug (I can't actually find the link now) with the driver for the wireless card in my laptop. I have installed 7.10 and it connects fine without any work at all so I guess I'll have to wait for this to be fixed before I can upgrade. Or I could try fix it myself....hmmmmmm

Install 8.04 with confidence.
I installed madwifi drivers version: "madwifi-nr-r3366+ar5007"
i found this driver, did the make, make install.... and it went well

You will need the build-essencial package.

---

