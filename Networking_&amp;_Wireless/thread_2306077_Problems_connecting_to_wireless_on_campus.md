---
title: "Problems connecting to wireless on campus"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by Stacey_Burton on 2015-12-12
Hello Everyone,

I am currently attempting to use Wi-Fi on campus unfortunately I am not having much luck connecting to it.  When I am at home and in other environments I have no problems connecting to wireless including those using captive portal to authenticate. 

I am using Ubuntu 14.04

Basic Trouble Shooting Steps Taken:
Rebooted
Restarted the interface
Tried manually configuring the wireless interface from the command line
Applied updates
Tried wifi radar instead of the onboard configuration client.
Checked login credentials to confirm that I was entering them correctly

The output from lspci is the following:
```
Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```

```
iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:08:aa:db  
          inet6 addr: fe80::6aa3:c4ff:fe08:aadb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236 (236.0 B)  TX bytes:190 (190.0 B)
```

The card seems to be working correctly.

I believe that I have the proper firmware installed as I know that this Wireless Adapter has been to known to have issues and not function properly while using Linux, so I tried to update it per the information that I found in other forum post.

Here is what I see when I try to connect................




[ATTACH=CONFIG]266101[/ATTACH][ATTACH=CONFIG]266102[/ATTACH]
All of my my M$ devices authenticate correctly and have no problem using the wireless on campus.

Does anyone know how to fix this issue?
.

---

### Post by QIII on 2015-12-12
Hello!

Have you conferred with the IT department on campus?

---

### Post by Stacey_Burton on 2015-12-12
> **QIII said:**
> Hello!

Have you conferred with the IT department on campus?

Thanks for responding.

Yes I have, he is looking into the problem on their end, however he does not an answer at this time. I am working in tandem with him by asking the linux gurus here.

---

### Post by QIII on 2015-12-12
Given that you are able to gain access at other points, I think it unlikely -- given that we don't know how the access is set up on campus -- that we will be able to divine the issue in the dark.

You may get lucky, though.

Best wishes!

(By way of forewarning:  If this turns out to be an issue of campus policy, we won't allow support in circumventing the rules.)

---

