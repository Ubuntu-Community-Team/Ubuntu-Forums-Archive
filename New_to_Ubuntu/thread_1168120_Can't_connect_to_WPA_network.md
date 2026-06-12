---
title: "Can't connect to WPA network"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-05-23
I'm trying to connect to a WPA-encrypted network. I've tried nm-applet and wicd, both to no avail. They accept the encryption key, but can't obtain an IP address (at least, that's what it looks like is happening).

I can connect fine on the same machine in Vista. Is there something I'm missing here?

Thank you!

---

### Post by Dill on 2009-05-23
Can you try to connect to the network, fail, and then post the output of ```
dmesg | tail
```

Cheers,
Dylan

---

### Post by doctorbighands on 2009-05-23
```
dmesg | tail
```

returns the following:

```

[   30.931356] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   30.934777] [drm:i915_setparam] *ERROR* unknown parameter 4
[   30.934805] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   32.790396] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   39.556020] eth1: no IPv6 routers present
[   40.154469] ieee80211_crypt: registered algorithm 'TKIP'
[   49.658936] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   56.844982] CPU0 attaching NULL sched-domain.
[   56.845065] CPU0 attaching NULL sched-domain.
[  115.403148] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

---

### Post by Dill on 2009-05-23
Hmm... from the line

```
[   40.154469] ieee80211_crypt: registered algorithm 'TKIP'

```

it looks like the encryption algorithm loaded, so it would seem at least that it got to the encryption process, but that's really just a guess. The

```
[  115.403148] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

message might also be problematic. I tried searching for that a bit and didn't find anything too useful. I believe most of the other errors are kernel specific and don't relate to networking, but perhaps a pro "dmesg parser" could provide more insight.

You could try a couple of things. To "refresh" your DHCP lease and get a new IP address, try 

```
sudo dhclient -r
```

to release, then

```
sudo dhclient
```

to renew.

You can also try disabling and reenabling your wireless card:

```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```

Also, what kind of a network card do you have?

```
lspci | grep Network
```

You may be able to try wpa_supplicant, which (as the name suggests), assists in WPA authentication: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

The document is a bit dated, but it should be a good start.

Cheers,
Dill

---

