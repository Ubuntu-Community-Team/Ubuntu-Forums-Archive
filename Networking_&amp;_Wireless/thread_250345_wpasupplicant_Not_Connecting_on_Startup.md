---
title: "wpasupplicant Not Connecting on Startup"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by bradlis7 on 2006-09-03
I've installed wpasupplicant, and it works, but on startup, it doesn't connect to the internet. I have to go to System->Administration->Networking, and disable eth0, and save it. I also have a problem there, because the screen doesn't close by itself, I have to click the 'X'; it's almost like it's waiting on something.

Here's my interfaces file without the comments:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
pre-up /sbin/wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

iface eth0 inet dhcp

```

I've tried to remove the eth0 code, but it doesn't seem to help me either. I think doing
```

ifdown -a
ifup -a

```
will work also, without actually disabeling eth0.

Any ideas would be helpful, thanks.

---

### Post by Zed on 2006-09-05
Do you have an /etc/default/wpasupplicant (not wpa_supplicant) that says ENABLED=1 like it advises [here](http://ubuntuforums.org/showthread.php?t=31418)? That's working for me with a setup that's otherwise like yours (but I'm also using the latest ndiswrapper and wpa_supplicant, built from source, not the standard Dapper packages.)

---

### Post by bradlis7 on 2006-09-06
Yeah, here's what I have:

```

ENABLED=1
OPTIONS="-iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w"

```

---

