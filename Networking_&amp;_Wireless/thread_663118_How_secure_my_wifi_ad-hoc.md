---
title: "How secure my wifi ad-hoc"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by zit on 2008-01-09
I made my computer a NAT server who share internet connection through a dongle bluetooth, wifi dongle & of course ethernet...

I'm a few noob in wifi but sharing wifi works and now i need to secure wifi sharing

Here my pc server wifi config interfaces :
```
auto wlan0
iface wlan0 inet static
address 192.168.*.*
netmask 255.255.255.0
pre-up iwconfig wlan0 mode Ad-Hoc
pre-up iwconfig wlan0 essid "your essid"
pre-up iwconfig wlan0 key "s:ab123"

```


Now i think i need to :
- Hidden Essid
- WPA2 TKIP encryption
- MAC filtering
- DHCP server off (already done)

Please how make this?

---------------------------------------------------------------------------------------------------------------
```
Just a discovered bug with my kubuntu gutsy and my linksys WUSB54GC (ndiswrapper rt73).

If you put iwconfig wlan0 key 123456789abcde or in interfaces file wireless-key 123456789abcde
you get on networking restart :
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

use 
iwconfig wlan0 key "s:ab123"
and it's ok ;)

I don't know if it's a ubuntu bug or hardware...
```

---

### Post by HermanAB on 2008-01-09
Why ad-hoc?  That is inviting trouble.

Hiding the ESSID and filtering the MAC only affects honest people - i.e. you make it inconvenient to yourself only.  It doesn't do anything to the 'bad guys'.

WPA is a good idea, if you can get it to work.  Otherwise WEP is better than nothing and way better than hiding the ESSID or filtering the MAC.

Cheers,

Herman

---

### Post by zit on 2008-01-10
i haven't success to make work mode managed.

It's not a inconvenient for me to use ESSID hidding & MAC filter.
I'll like to use it even if you said it's placebo.

So wpa is important to use. How do it for my config?

if anybody can help?

---

### Post by Hightide on 2008-01-10
this tutorial may help
:)

---

### Post by HermanAB on 2008-01-10
The problem is that the ESSID and MAC is in *every* packet. It has to be.  It is part of the protocol.  So hiding or filtering on it accomplishes nothing.

---

### Post by zit on 2008-01-10
> **Hightide said:**
> this tutorial may help
:)

Wich tutorial please?

---

