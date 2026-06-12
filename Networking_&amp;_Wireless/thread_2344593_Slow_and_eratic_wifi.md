---
title: "Slow and eratic wifi"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2016-11-26
Folks,

I'm running 16.04 64bit on a Toshiba laptop - my previous 12.04 wifi was very stable to strangely 16.04 I get occasional disconnect issues and speeds are slower than my mobile phone.

I have two repeaters (Orion and Cassiopeia) from my main Access Point Andromeda, my 16.04 will not connect to my main access point but will connect to a repeater.

I was asked to supply info from a wifi script, the read out says it exceeds Ubuntu's text file limit so is attached as an archive as follows.

[ATTACH]272403[/ATTACH]

Geoff

---

### Post by Geoff_Lane on 2016-11-26
Further to my post - just lost connection completely. Did the following;

> sudo service network-manager restart

and lost wifi completely, no access points showed at all, repeated command around three times and could not get any access points to show and 'Enable Networking' was greyed out.

Reboot got it going again.

Geoff

---

### Post by jeremy31 on 2016-11-26
I would start by disabling fwlps as it usually fixes Realtek wifi in Ubuntu
```
echo "options rtl8821ae fwlps=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```

Reboot

There does appear to be some user restrictions in Network Manager for the repeaters but not for andromeda

---

### Post by Geoff_Lane on 2016-11-27
> **jeremy31 said:**
> I would start by disabling fwlps as it usually fixes Realtek wifi in Ubuntu
```
echo "options rtl8821ae fwlps=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```

Reboot

There does appear to be some user restrictions in Network Manager for the repeaters but not for andromeda

OK, done that and I'll report back.

Geoff

---

