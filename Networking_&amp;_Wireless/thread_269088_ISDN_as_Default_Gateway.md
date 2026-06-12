---
title: "ISDN as Default Gateway"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by thesmartace on 2006-10-01
A friend of mine wanted to try out Ubuntu so I installed it for them (Dual booted with WinXP).

The only problem I had with the computer was that it used ISDN for internet via a usb NT1 Plus II. This itself wasn't overly the problem. I used wvdialconfig to set up wvdial and edited the generated config file to input the user/pass and the phone number. It connected fine (showed up in Networking and the lights on the modem indicated it was connected) but Ubuntu didn't seem to want to use it as the default gateway.

They only way I could get it to work was to manually set the default gateway each time it connected.

```
sudo route del default gw <eth0 gateway ip>
sudo route add default gw <telstra remote ip>
```

The internet worked fine once I had done this but it needed to be done again every time they restarted the computer. It would be nice to have Ubuntu remember the default gateway (the only available option in Networking is eth0).

Any ideas?

---

