---
title: "New mac80211 based wlan drivers?"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by crys on 2007-07-31
Hi,

to get rid of wpa_supplicant I thought to give the newly introduced mac80211 system a try. I have a rtl8187-based wireless card and since kernel 2.6.23-rc1 there is support included for this chipset.

When I boot the 2.6.23-rc1 kernel it perfectly finds the card but I have no clue how to set up WPA TKIP with PSK access to my AP.
It seems Google doesn't know it either.

Did anybody get this stuff working?

Thanks,
Chris

---

### Post by noob12 on 2007-08-01
Does **iwpriv** work?

---

### Post by thomasf on 2007-08-01
Hi!

I tried to use new, mac80211 driver for rtl8187 on 2.6.23rc1 kernel. I set up WPA supplicant in order to enable WPA encryption. Unfortunately, it seems that connection is not stable. After some time, dmesg shows a problem - RX decryption failed or something like that. Despite of this error msg, connection is maintained. But not for a long time. Eventually it ceases to work - without additional warnings.

```
iwpriv

wlan0     Available private ioctls :
          param            (8BE0) : set   2 int   & get   0      
          get_param        (8BE1) : set   1 int   & get   1 int  
```

---

### Post by crys on 2007-08-02
Well, my intention to use the mac80211 driver was to avoid this mess with wpa_supplicant. rtl8187_mac80211 should be able to do wpa natively without wpa_supplicant.
The problem is that I don't know the exact iwpriv command to set up wpa, tkip and psk.

Any ideas?

Chris

---

### Post by noob12 on 2007-08-02
I don't know that much about this, but I would have expected it implements the conventional wireless extensions ioctls  so that it would operate with tools in the same way.  Have you already tried "conventional" configuration, using either NetworkManager or /etc/network/interfaces (as in [the sticky HOWTO on this forum]("http://ubuntuforums.org/showthread.php?t=318539")).

Typing **iwpriv** with no args will list the private ioctls, but in general one has to look at driver docs for the description of these; the driver may have a man page which describes these.

---

### Post by crys on 2007-08-03
As thomasf mentioned, there are two ioctls. Unfortunately there is no docu for the driver and no man page...

---

### Post by crys on 2007-08-03
OK, it finally works now! I did the wpa setup with networkmanager.

---

