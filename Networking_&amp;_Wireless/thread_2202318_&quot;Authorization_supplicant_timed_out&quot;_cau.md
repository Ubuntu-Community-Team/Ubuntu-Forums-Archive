---
title: "&quot;Authorization supplicant timed out&quot; causes repeated wifi drops"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by xmbwd on 2014-01-28
I am running Kubuntu 13.10 on an ASUS Q501LA with an Intel 7260 wireless card.  I have four wireless routers around the house (various reasons, but mostly b/c it is an old house with lathe and plaster walls inside and stucco over mesh outside, so signal is hard to pass).  Each router is running either Tomato or DD-WRT and has the same SSID, on the same channel.  As I move around the inside and outside of the house, the computer *should* hand off to the stronger signal -- and I can tell which router the Asus is connected to by viewing the BSSID.    

My problem right now is that, even staying stationary in a single location with a "decent" signal, the connection drops and I get an "**Authorization supplicant timed out**" message.  This happens every hour or so when stationary, but more frequently when I move around.  

Here is the output from lspci -nnk | grep -iA2 net:

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
        Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
        Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
        Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4160]
        Kernel driver in use: iwlwifi
```


Is there a way to fix this?  I believe that "supplicant" here means  "client," which would be my Kubuntu laptop.  So I think that is where  the problem lies (that and the Asus doesn't experience this problem when it is running Windows).

Thanks for any help and/or suggestions.

---

### Post by chili555 on 2014-01-28
Are you using the latest firmware? [http://askubuntu.com/questions/411475/problem-with-the-intel-wireless-7260-driver/411515#411515](http://askubuntu.com/questions/411475/problem-with-the-intel-wireless-7260-driver/411515#411515)

---

### Post by xmbwd on 2014-01-28
Thanks!  I tried the firmware upgrade for the Intel Corporation Dual Band Wireless-N 7260 and and it seems to be working.  I will post back if it persists after upgrading to the latest firmware for my Intel card. 

Thanks again -- I would have been stuck looking at authorization and supplicant results forever.

---

### Post by chili555 on 2014-01-28
> **xmbwd said:**
> Thanks!  I tried the firmware upgrade for the Intel Corporation Dual Band Wireless-N 7260 and and it seems to be working.  I will post back if it persists after upgrading to the latest firmware for my Intel card. 

Thanks again -- I would have been stuck looking at authorization and supplicant results forever.It's what we do! Keep us posted and post back if it isn't completely fixed.

---

### Post by xmbwd on 2014-01-29
Well . . . unfortunately, it did not work.  I am in a stationary position, in good range with good signal (-53) and quality (55).  But it keeps dropping out with the "Authorization supplicant timed out" error.   

Other suggestion/ideas greatly appreciated!

---

### Post by chili555 on 2014-01-29
Could we see more of the log, say 6 lines before and 6 after that message? Also, does Power Management appear on or off?```
iwconfig
```

---

### Post by xmbwd on 2014-01-29
I appreciate the continued help.  Power management is off as reported in iwconfig:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"dd_wrt"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:96:05:AF   
          Bit Rate=117 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:8   Missed beacon:0
```

Sorry, but I'm not sure which log to look in for the error.  Here is the last few lines dmesg:

```

[275136.729877] wlan0: authenticate with 00:1c:10:3b:xx:xx
[275136.730741] wlan0: send auth to 00:1c:10:3b:xx:xx (try 1/3)
[275136.732749] wlan0: authenticated
[275136.734921] wlan0: associate with 00:1c:10:3b:xx:xx (try 1/3)
[275136.739434] wlan0: RX AssocResp from 00:1c:10:3b:xx:xx (capab=0x411 status=0 aid=2)
[275136.748432] wlan0: associated
[275146.744346] wlan0: disassociating from 00:1c:10:3b:xx:xx by local choice (reason=3)
[275146.747929] wlan0: deauthenticating from 00:1c:10:3b:xx:xx by local choice (reason=3)
[275146.748258] cfg80211: Calling CRDA to update world regulatory domain
[275146.754361] cfg80211: World regulatory domain updated:
[275146.754369] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[275146.754374] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275146.754379] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275146.754382] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[275146.754386] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275146.754389] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275151.447725] wlan0: authenticate with c0:c1:c0:96:xx:xx
[275151.448901] wlan0: send auth to c0:c1:c0:96:xx:xx (try 1/3)
[275151.453112] wlan0: authenticated
[275151.453953] wlan0: associate with c0:c1:c0:96:xx:xx (try 1/3)
[275151.457719] wlan0: RX AssocResp from c0:c1:c0:96:xx:x (capab=0x411 status=0 aid=2)
[275151.463222] wlan0: associated
[275152.572606] wlan0: deauthenticating from c0:c1:c0:96:xx:xx by local choice (reason=3)
[275152.577859] cfg80211: Calling CRDA to update world regulatory domain
[275152.586365] cfg80211: World regulatory domain updated:
[275152.586369] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[275152.586370] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275152.586372] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275152.586373] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[275152.586374] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275152.586376] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[275214.684914] CIFS VFS: Server 10.0.1.2 has not responded in 120 seconds. Reconnecting...
[275214.688575] CIFS VFS: Server 10.0.1.8 has not responded in 120 seconds. Reconnecting...
```

Please let me know if there is some other log that would help. 

The CIFS errors are because once the wifi goes down, I lose my network mounts.

(I *really* doubt this is related, but I just noticed that I can't open MS Word via PlayOnLinux when the wireless is down).

---

### Post by chili555 on 2014-01-30
It appears to roam from one AP to the next, the behavior you want and need, but doesn't...quite...lock on. Let's try a few things and see if we can help it.  Some things that may be helpful are to disable 802.11N capability. Please open a terminal and do:

```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
modprobe -r iwldvm
modprobe -r iwlwifi
modprobe iwlwifi
exit

```
Some users seem to be helped by explicitly setting the regulatory domain from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) For instance, if your country code is ES, then:

```
gksudo gedit /etc/rc.local
```

Right above the line exit 0, add a new line:

```
iw reg set ES
```

Of course, substitute your code here. After a reboot, is there any improvement?

---

### Post by xmbwd on 2014-01-30
Thanks Chili.  You're absolutely right:  I want and need the roaming from AP to AP, but preferably only when I move the laptop or one signal drops below a usable threshold.  

I made your suggested mods, but I won't be able to test until tomorrow.  Will post back with results.  Hopefully good ones.

---

### Post by xmbwd on 2014-01-30
Somehow, that really messed things up.  Now I can't connect to some of  my APs at all.   It keeps acting like I didn't give it the password.  I  get a secrets error and the KDE Daemon keeps popping up asking for my  keychain password.

Here is the dmesg for the one I can connect to:
```

[   87.537732] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   87.537736] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   87.541037] wlan0: associate with 94:44:52:a6:da:c6 (try 1/3)
[   87.546130] wlan0: RX AssocResp from 94:44:52:a6:xx:xx (capab=0x411 status=0 aid=2)
[   87.549913] wlan0: associated
[   87.549964] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Here is what I get for the AP I can't connect to (which happens to be the stronger signal!):

```
[  257.180752] wlan0: 94:44:52:a6:xx:xx denied association (code=18)
[  257.195417] wlan0: deauthenticating from 94:44:52:a6:xx:xx by local choice (reason=3)
[  257.341089] wlan0: authenticate with 00:1c:10:3b:xx:xx
[  257.346110] wlan0: send auth to 00:1c:10:3b:xx:xx (try 1/3)
[  257.347922] wlan0: authenticated
[  257.350392] wlan0: associate with 00:1c:10:3b:xx:xx (try 1/3)
[  257.352907] wlan0: RX AssocResp from 00:1c:10:3b:xx:xx (capab=0x411 status=18 aid=0)
[COLOR=#ff0000]**[  257.352920] wlan0: 00:1c:10:3b:xx:xx denied association (code=18)**[/COLOR]
[  257.379200] wlan0: deauthenticating from 00:1c:10:3b:xx:xx by local choice (reason=3)
```

This is bad.  I can't connect to my best AP.  

Retracing my steps, when I tried:
```
modprobe -r iwlwifi
```

I got back:

```
FATAL: Module iwlwifi is in use.


```

So I tried:

```
rmmod iwlwifi
```

Which gave me:

```
Fatal:  Module iwlwifi is in use by:  iwlmvm.
```

So I tried:

```
rmmod iwlmvm
```

Then started over with the modprobe steps in your instructions. And I  got through those with no errors.  I also included "iwlmm."  

But now I have the problem of not being able to connect to my best AP.   Aaaaaaaaaaarrrrrrrrrgghhhhhh!!

Any ideas on how to fix?   Restart did not do it.

---

### Post by xmbwd on 2014-01-30
I'm leaving the post above up, rather than editing it, in case someone else has this happen. 

But the explanation in my case was easy -- just took a second to actually think!

When I did this:
```
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf 
```

I turned the ability to receive wireless N off (yeah, I know, that's what you said it would do!).  But I forgot that I have all my routers, except one, to run solely on the N channel.  So ... turning off N access from the Laptop made all those APs inaccessible.  DUH!  To fix, I just:

```
echo "options iwlwifi 11n_disable=0"  >>  /etc/modprobe.d/iwlwifi.conf 
```

I will check if setting the country code, alone, works and get back to you.  Thanks again for your help!

---

### Post by chili555 on 2014-01-31
> But I forgot that I have all my routers, except one, to run solely on the N channel. The driver *iwlwifi* is troubled by N in many, perhaps most cases. I myself have such a device and it works fine at N speeds and so I have begun to believe that it isn't so much the hardware-driver combination, but rather the hardware-driver-router combination that is troublesome.

We will be very interested in your further explorations. I hope you are not asking for the, so far, impossible to become possible.

---

### Post by xmbwd on 2014-01-31
Am I reading you correctly that I will have to turn off N and go solely with G if I want to fix this issue?

Unfortunately, setting the locale alone did not resolve the problem.  Here is my latest dmesg that, I think, is new:

```
[32095.819661] wlan0: authenticated
[32095.819954] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32095.819966] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32095.823165] wlan0: associate with 94:44:52:a6:da:c6 (try 1/3)
[32095.825977] wlan0: RX AssocResp from 94:44:52:a6:xx:xx (capab=0x411 status=0 aid=2)
[32095.834580] wlan0: associated
```

If necessary, I can move back to G only.  But that seems kind of lame.

---

### Post by chili555 on 2014-01-31
> Am I reading you correctly that I will have to turn off N and go solely with G if I want to fix this issue?
There are some routers that work perfectly well with 802.11N and iwlwifi; my Linksys EA6300 for one example. Most do not, including, evidently, your Tomatoes and DD-WRTs. 

You could and should try every combination of settings in the router, including fixed vs. auto channel, fixed channel on 1, 6 or 11, etc. A quick scan will tell you who's on what channel nearby:```
sudo iwlist wlan0 scan
```I agree with you, it is lame. I'm quite certain there is a lot of finger pointing between the router manufacturers and Intel. 

Here is what Intel says about the infamous 6235: [https://communities.intel.com/message/192239#192239](https://communities.intel.com/message/192239#192239) and their suggestions: [https://communities.intel.com/message/214103#214103](https://communities.intel.com/message/214103#214103) Sporadic but recurring connection drops, they say??

The driver/device/router combinations are imperfect. The only technique I have found, by trial and error, that seems to work is 'options iwlwifi 11n_disable=1.' I wish I had something better. I have volunteered on several forums for many years and I have been and continue to be frustrated by this problem.

---

### Post by xmbwd on 2014-01-31
Thanks Chilli.  That sucks.  I will try some different combinations.

---

