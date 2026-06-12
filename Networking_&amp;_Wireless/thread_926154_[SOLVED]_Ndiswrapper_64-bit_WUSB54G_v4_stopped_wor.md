---
title: "[SOLVED] Ndiswrapper 64-bit WUSB54G v4 stopped working after upgrade"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by the_weekend on 2008-09-21
> **the_weekend]
As stated, I have a WUSB54G v4. Ndiswrapper still recognizes it and everything seems normal except for actually connecting via the new Network Manager interface. I'm running 64-bit ubuntu and am using a 64-bit windows drive under ndiswrapper. I tried reinstalling ndiswrapper with a manual compile. I tried switching back to the native RT2570 driver, but it is also no longer working. Could there be a problem with the new Network Manager? What else should I try?
[/QUOTE]

[QUOTE=pytheas22 said:**
> There are a few things to try.  First, can you connect if you use [wicd]("http://wicd.sourceforge.net") instead of Network Manager?  Second, if you boot to an older kernel (you should have several kernels to choose from at the grub boot menu that you see when you start your computer), do things work?   Third, if you're using encryption, can you connect with it disabled?

Are you sure that ndiswrapper is still driving the card, not rt2570?  You can tell by looking at the output of 'lshw -C Network'.

If you can't figure this out, please open up a new thread (just so that things don't get too confusing here) and let me know the URL, and I'll respond there.

So the rt2570 drivers are still blacklisted and ndiswrapper is still loaded. The card seems to run fine lights a-blinkin' when I'm trying to connect. The old kernel doesn't work and I'm led to believe it's the new network manager giving me problems. Not sure I want to installe wicd, that'll take some trickery to get installed without internet and I'd prefer the stock manager if I can get it to work...

---

### Post by the_weekend on 2008-09-21
Wow, WICD did the trick. Thanks Pytheas!

---

### Post by pytheas22 on 2008-09-21
Glad that did it :)  Network Manager does have a reputation for being sort of buggy, and the way that it tries to negotiate WPA connections especially tends to be problematic (it tries to do it all on-the-fly instead of using the more traditional wpa_supplicant approach with a fixed configuration file).  wicd is usually more reliable, if a bit less convenient to use.

---

