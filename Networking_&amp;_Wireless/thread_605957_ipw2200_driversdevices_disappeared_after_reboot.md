---
title: "ipw2200 drivers/devices disappeared after reboot"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by rmills on 2007-11-07
I'm on a dual boot system, XP and Ubuntu on a Dell 700m with the Intel PRO/Wireless 2200 card.  Last night Ubuntu was able to connect flawlessly to my wireless router sporting WEP and MAC filtering.  After booting into Windows to reprogram my Harmony remote, then switching back to Ubuntu, my wireless card isn't showing up as an active device:

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

It's clearly not showing up in my network devices.  The drivers seem to be loading:

```
ieee80211              35656  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
```

I tried removing the ipw2200, ieee80211, and ieee80211_crypt modules and rebooting (something that used to work with an old version -i think hoary) but that didn't help.  The modules reappeared, but the device still wasn't listed.  Any help?  Please?

After checking dmesg, I noticed this:
```

[   17.788000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.096000] ipw2200: Unable to load ucode: -62
[   18.096000] ipw2200: Unable to load firmware: -62
[   18.096000] ipw2200: failed to register network device
[   18.096000] ipw2200: probe of 0000:02:01.0 failed with error -5
```

---

