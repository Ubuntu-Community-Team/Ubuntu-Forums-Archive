---
title: "WG511 install issues"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by cancel.man on 2006-09-02
I've been playing with this all day and it's driving me nuts...
The wireless card is a [Netgear WG511]("http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG511.aspx") (v1, I assume, because there's no other version stamped on it). I'm using the 3.00 drivers (netwg511.inf) available from the site.

After much ado and tips from several sites and forum threads ([this]("http://www.ubuntuforums.org/showpost.php?p=403257&postcount=2") being one of the more straight-forward), I finally got ndiswrapper to show up with ```
Installed ndis drivers:
netwg511                driver present, hardware present
```When I remove the card, ndiswrapper no longer claims the hardware is present, so I'm reassured by this- all seems good on that front. I also followed the rest of the steps in that reply (using -m and modprobe).

Unfortunately, the card still isn't working as far as I can tell. It shows up as eth1 in the Network Settings (as it always has), but when activated doesn't seem to even attempt to do anything. Also, the indicator lights have never lit (with Ubuntu) so that tells me there's something up.

Any ideas or suggestions?

Not sure if it helps, but iwconfig is showing this: ```
eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Still very new to Linux/Ubuntu, so the simpler the instructions the better, thanks.

---

### Post by cancel.man on 2006-09-03
Still looking for some assistance/insight into this issue. I'm sure there are plenty of things I haven't taken into consideration in troubleshooting (very new to Ubuntu/Linux), so any ideas or advice is appreciated.

One thing I've attempted since first posting the above is blacklisting other drivers (based on [this post]("http://www.ubuntuforums.org/showthread.php?t=192588")), but I'm really not sure what driver I should be blacklisting- as far as I can tell the driver it's using (even after using ndiswrapper to install the correct driver) is prism54, but I could be wrong and every time I blacklist prism54 the card is no longer visible on the Network Settings menu. How do I know what driver the card is attempting to use? Would this even be my issue?

---

