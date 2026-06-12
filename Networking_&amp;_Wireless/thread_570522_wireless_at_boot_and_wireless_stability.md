---
title: "wireless at boot and wireless stability"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by pug on 2007-10-08
I went ahead and installed Ubuntu 7.10beta on my mac mini.

Everything seems to be in working order except for a few things:

a) I was unable to setup wireless network at boot, e.g. wireless network would ONLY become active after I logged in (using the GUI, console login doesn't do squat).

Is there an easy way to set this up? I really need wireless to be active before I login...

So far what I've done is to manually edit stuff after reading up on it on the net and using a day on it...

/etc/network/interfaces
```

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-ssid ***
wpa-key-mgmt WPA-PSK
wpa-psk "***"

```

Which works fine, for about 5 minutes, after which the wireless network breaks down and I have to do a /etc/init.d/networking restart - after which it will work for 5 more minutes...

I know the access point is working as it was running like a charm when I was using OS X.... With network-manager the connection would come back up (well, sometimes, sometimes not heh). 

So - how do one go about getting a stable wireless connection that functions without being logged into the GUI?

-pug

---

### Post by scrooge_74 on 2007-10-08
you could try an earlier version of Ubuntu , I also have a couple of systems already online before I sign, but using 6.06

---

### Post by pug on 2007-10-08
6.06 is too old for me, trying to setup a mythtv box heh.

I'll give 7.04 a try, but I doubt it will be different..

---

### Post by scrooge_74 on 2007-10-08
7.04 could be less buggy, in my case even 7.04 was to buggy for my taste

Good luck with the setup

---

