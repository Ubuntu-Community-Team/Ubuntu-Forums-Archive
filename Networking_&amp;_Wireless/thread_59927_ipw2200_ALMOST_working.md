---
title: "ipw2200 ALMOST working"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by EndianX on 2005-08-25
Hey everybody.  I am having some trouble getting my wireless working, at least with wpa encryption.

I followed [this guide](http://ubuntuforums.org/showthread.php?t=26623) and it almost works, except the connection seems to be going up and down.

One second iwconfig gives this...
```

eth1      IEEE 802.11g  ESSID:"b7ar*i6a"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:10:62:9B:08
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-50 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon

```
The next second I get this...
```

eth1      unassociated  ESSID:"b7ar*i6a"
          Mode:Managed  Channel=0  Access Point: 00:13:10:62:9B:08
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
And then a few seconds later its working again.

Edit: Even when I have a signal, pings to the gateway give "Destination Host Unreachable"

Any idea what would cause this.  I am very new to Linux and just can't figure it out.

Thanks,

EndianX

---

### Post by luca_linux on 2005-08-26
Do these issues happen with or without wpa?
What AP have you got?

---

### Post by EndianX on 2005-08-26
[QUOTE=luca_linux]Do these issues happen with or without wpa?
What AP have you got?[/QUOTE]

I only have these with WPA.  Or at least, when I turn off all encryption, it works.  I have not tried WEP though.

What is an AP? :-X

---

### Post by luca_linux on 2005-08-26
[QUOTE=EndianX]I only have these with WPA.  Or at least, when I turn off all encryption, it works.  I have not tried WEP though.

What is an AP? :-X[/QUOTE]
 Ok, so it's a wpa issue.
AP stands for Access Point, that is the wireless router. :-P
Anyway, could you post your /etc/wpa_supplicant.conf?

---

### Post by ape on 2005-08-26
This is the same symptoms that I had using the ipw2200 driver and WPA.  The fix for me was to force the usage of the TKIP protocol rather than the default of CCMP.

I added the following lines to the network{} section of my wpa_supplicant.conf file:

         pairwise=TKIP
         group=TKIP

---

