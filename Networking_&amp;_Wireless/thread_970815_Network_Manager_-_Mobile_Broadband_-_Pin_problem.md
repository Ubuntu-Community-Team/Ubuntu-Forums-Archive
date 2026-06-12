---
title: "Network Manager - Mobile Broadband - Pin problem"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by CbrPad on 2008-11-04
I've done a fresh install of Intrepid and while it picks up my Huawei E220 modem fine and even has my operator details, every time I try to connect I get a 'Network disconnected' error.

The problem seems to be that NM isn't passing the Pin code to the modem.  If I configure a wvdial.conf to pass the pin, run that, disconnect and then try to connect using NM it connects properly next time.

I was running the ppa Network Manager on Hardy and everytime I ran NM it asked me for the Pin and then connected no probs, but is failing now in Intrepid.

Any ideas ??

---

### Post by theCroc on 2008-11-09
I have exactly the same issue. Ran NM 0.7 in hardy and it asked for pin and connected fine with my huawei e220. In intrepid it just wont connect. It doesn't even ask for the pin.

---

### Post by CbrPad on 2008-11-09
Here ya go, this is how I got around it eventually, I could disable the pin using Umtsmon and now it's fine at last, but what a serious pain if you didn't have any other web access.

[http://ubuntuforums.org/showthread.php?t=938686&page=2](http://ubuntuforums.org/showthread.php?t=938686&page=2)

---

