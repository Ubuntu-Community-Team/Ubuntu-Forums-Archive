---
title: "My Journey Towards Wireless (Atheros 5006x)"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by amrish on 2007-11-05
I've done my homework and searched the forum up and down making sure I tried everything before I started my own post and as consolation I will be sure to organize and document the steps I've taken that got this problem solved so other's can benefit.

Alright so here goes...

Things I've tried.... in the order I've tried them

**Tried** default drivers.
**Result** Able to see networks and attempt a connection to them, no wireless connection is made though.

**Tried** using 'ndiswrapper' w/ drivers that did work in Windows XP
**Result** I could see and attempt a connection to my network, but unable to lock in a connection

**Tried** installing madwifi tools and going to the website to follow their guide on how to set stuff up.
**Result** No difference.
**Conclusion**I'm not able to get an IP address

**Tried** installing [Wicd]("http://wicd.sourceforge.net/")
**Result** No difference.
**Conclusion**Further concluded that I can't get an IP from my wireless router, cause it stays showing that on the GUI until it stops.

**Tried** updating my MadWifi drivers to the very latest drivers.
**By doing:** I stopped ath_pci, ran the uninstall script, then with the latest MadWifi from their website 0.9.9.3, and installed that.
**Result** No difference.

**Tried** After everything I always try to manually access the DHCP using "dhclient ath0"
**result** unable to bind to an IP

**Tried** Using Wicd to set a static IP address for my wireless connection
**Result** I am able to connect, but no connection is really there, I can't get to the router or the internet through my router.


**Other notes** I am able to easily get a wired connection, that's what I'm on, and I disabled WPA/TKIP on my network to simplify things and work one issue out at a time.

**Output of "iwconfig"**
```

ath0      IEEE 802.11g  ESSID:"We Love Our Router"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: < Actual HWaddr removed >
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-35 dBm  Noise level=-93 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I can confirm that the HWaddr is the correct one that my Router actually is. so that's working.

Alright, well I'm ready for anyone who's ready to help me and I'll be sure to document results.

Thanks everyone!

---

### Post by amrish on 2007-11-06
Day 2:

No progress, fumbled around with what I did on Day one, repeating things, no progress at all.
Still no connectivity.

** Update **
I was able to find out that Atheros model numbers are generally a complete mess and drivers identify themselves as the wrong chipset.
I have a 168c001c, which I'm not actually sure what that is. I'm thinking 5006exs

**Tried** [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
**Result** Same issue. Still cannot obtain an IP


** Well for now I'm done, I can't stand the frustration anymore, won't boot up this Ubuntu or try anything unless I get some fresh ideas. ** no point using it unless I have WiFi.

---

