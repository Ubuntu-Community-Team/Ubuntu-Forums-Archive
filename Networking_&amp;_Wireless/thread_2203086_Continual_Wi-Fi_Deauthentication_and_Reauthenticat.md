---
title: "Continual Wi-Fi Deauthentication and Reauthentication"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by sam30 on 2014-02-01
I've found many other posts with people describing similar problems, but none of the solutions worked or seemed to apply to me (different hardware, etc)  

I upgraded to Kubuntu 13.10 this morning, and I now have some annoying wi-fi related issues. Every ~1 - 10 minutes the system notification system tells me that my wireless is being deactivated. For every one of these notifications, the following series of messages are added to dmesg: 

 ```
[Sat Feb  1 14:30:13 2014] wlan0: authenticate with 44:94:fc:90:af:5f 
[Sat Feb  1 14:30:13 2014] wlan0: send auth to 44:94:fc:90:af:5f (try 1/3) 
[Sat Feb  1 14:30:13 2014] wlan0: send auth to 44:94:fc:90:af:5f (try 2/3) 
[Sat Feb  1 14:30:13 2014] wlan0: send auth to 44:94:fc:90:af:5f (try 3/3) 
[Sat Feb  1 14:30:13 2014] wlan0: authentication with 44:94:fc:90:af:5f timed out 
[Sat Feb  1 14:30:20 2014] wlan0: authenticate with 44:94:fc:90:af:5f 
[Sat Feb  1 14:30:20 2014] wlan0: send auth to 44:94:fc:90:af:5f (try 1/3) 
[Sat Feb  1 14:30:20 2014] wlan0: authenticated 
[Sat Feb  1 14:30:20 2014] wlan0: associate with 44:94:fc:90:af:5f (try 1/3) 
[Sat Feb  1 14:30:20 2014] wlan0: RX AssocResp from 44:94:fc:90:af:5f (capab=0x31 status=0 aid=4) 
[Sat Feb  1 14:30:20 2014] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated 
[Sat Feb  1 14:30:20 2014] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement) 
[Sat Feb  1 14:30:20 2014] wlan0: associated [Sat Feb  1 14:30:30 2014] wlan0: disassociating from 44:94:fc:90:af:5f by local choice (reason=3) 
[Sat Feb  1 14:30:30 2014] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated 
[Sat Feb  1 14:30:30 2014] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement) 
[Sat Feb  1 14:30:30 2014] wlan0: deauthenticating from 44:94:fc:90:af:5f by local choice (reason=3)
```  

So, it tries to authenticate with the router ~4 times, finally succeeds, then it associates, and then immediately disassociates and deauthenticates. This will then repeat itself every few minutes. All the while, I am able to use internet.  

Also, every now and then the KDE Daemon will jump up and have me put in my wi-fi password...  My laptop has its own internal wi-fi card (I believe that's the brcmsmac?). I also have a USB network jimmy, model TP-Link LT-WN722N, which seems to improve signal strength, even though I never found and installed any drivers for it... I just leave it there for good luck. 

 I'm far from knowledgable about this stuff; my main priority is to get rid of the constant system notifications & entering my wifi password. Thanks!

---

### Post by Julian Lewis on 2014-02-01
Same here on my HP ---
I also upgraded to 13.10 on my HP just now 
Linux jhp 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686 i686 i686 GNU/Linux
It goes round and round doing this at startup - eventually it stops and I get wlan working

```

[  141.715767] wlan0: authenticate with 32:b0:5d:a8:e2:49
[  141.719580] wlan0: send auth to 32:b0:5d:a8:e2:49 (try 1/3)
[  141.824317] wlan0: send auth to 32:b0:5d:a8:e2:49 (try 2/3)
[  141.826192] wlan0: authenticated
[  141.828294] wlan0: associate with 32:b0:5d:a8:e2:49 (try 1/3)
[  141.832404] wlan0: RX AssocResp from 32:b0:5d:a8:e2:49 (capab=0x411 status=0 aid=1)
[  141.852362] wlan0: associated
[  149.108689] wlan0: deauthenticating from 32:b0:5d:a8:e2:49 by local choice (reason=3)

```

Interesting but could this be related to ip6 ?

```

wlan0     Link encap:Ethernet  HWaddr 10:0b:a9:02:69:ac  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::120b:a9ff:fe02:69ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1091944 (1.0 MB)  TX bytes:248630 (248.6 KB)

```

---

### Post by sam30 on 2014-02-01
I have an HP laptop as well. I think there's some incompatability with the internal Broadcom network cards...  We have the same OS version:
```
Linux lombard-command 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686 i686 i686 GNU/Linux
```
Is it possible to delegate all wifi duty to the USB module (TL-WN722N)?

---

