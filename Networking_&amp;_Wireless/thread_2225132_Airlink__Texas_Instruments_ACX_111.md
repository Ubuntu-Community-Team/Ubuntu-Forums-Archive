---
title: "Airlink / Texas Instruments ACX 111"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by angel10 on 2014-05-20
Hello everyone

Recently I installed a fresh LinuxCNC distribution on a computer. I had an old Airlink wireless card and managed to get it to work using ndiswrapper. I felt proud of myself although I did not really know what I was doing. Then after a few days I followed Linux advice to upgrade from 10.04 to 12.something and the wireless connection disappeared.

If I do

```
lspci -nn -d 104C:9066
```

I get the following:

```
00:0a.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
```

If I open Windows Wireless Drivers I see tnet1130; Hardware present? Yes. But the wireless device does not show up on network connections.

Any help to relief my deep frustration will be sincerely appreciated.

- Angel

---

### Post by angel10 on 2014-05-20
Never mind, I'll install 10.04 again.

---

### Post by Vladlenin5000 on 2014-05-20
You had probably updated to the next LTS version, 12.04 (supported until 2017). You also have the choice of the new 14.04 (supported until 2019). The old 10.04 you had is indeed EoL (end of life), no longer supported, ie, no security updates or others, etc.
My suggestion is to _keep_ either of the _LTS_ versions currently support and _obtain a new wi-fi device_ because that one is so old it simply isn't worth it.

---

### Post by tgalati4 on 2014-05-20
Using [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") should work to install the driver in either 12.04 or 14.04.  You just need some patience, some reading, and the WindowsXP driver.  Follow the instructions for ndiswrapper.

---

