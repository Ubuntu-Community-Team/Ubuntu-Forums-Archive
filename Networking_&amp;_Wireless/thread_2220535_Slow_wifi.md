---
title: "Slow wifi"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by insane9 on 2014-04-28
I dual-boot my laptop with Windows 8.1 and Ubuntu 14.04 LTS. My problem is that my wi-fi is very slow on Ubuntu 14.04 compared to when I am logged into Windows.

My wifi card is a [SIZE=2][COLOR=#000000]R[/COLOR][COLOR=#000000]ealtek RTL8188EE[/COLOR][COLOR=#000000]. I've tried to install the driver as post #11 suggested in this thread: [/COLOR][/SIZE]http://ubuntuforums.org/showthread.php?t=2162026

However I get the following error when I typed '[FONT=Ubuntu Mono]make defconfig-rtlwifi[/FONT]' into the terminal:

```

/home/si/Desktop/backports-3.11-rc3-1/net/wireless/sysfs.c:151:2: warning: initialization from incompatible pointer type [enabled by default]
/home/si/Desktop/backports-3.11-rc3-1/net/wireless/sysfs.c:151:2: warning: (near initialization for &#8216;ieee80211_class.suspend&#8217;) [enabled by default]
make[6]: *** [/home/si/Desktop/backports-3.11-rc3-1/net/wireless/sysfs.o] Error 1
make[5]: *** [/home/si/Desktop/backports-3.11-rc3-1/net/wireless] Error 2
make[4]: *** [_module_/home/si/Desktop/backports-3.11-rc3-1] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2



```

Can anyone help?

Thanks

EDIT: Seems to be fixed by installing the 3.14 Kernel, see post #7 here: [http://ubuntuforums.org/showthread.php?t=2218962](http://ubuntuforums.org/showthread.php?t=2218962)

---

