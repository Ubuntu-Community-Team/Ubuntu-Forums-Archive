---
title: "MSI Notebook RealTek wireless driver"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by mckelly46 on 2008-11-07
Hello all,

I've tried all the recommended actions to get my MSI Wind wireless running but I've had no luck. It's a RealTek RTL8187SE PCI Express Card.

I was wondering if a Synaptic Package Manager solution is a possibility - if not now, then in the future?

Cheers,

---

### Post by Zorael on 2008-11-07
What recommendations did you follow? Please summarize what you've done so far. :3

---

### Post by mckelly46 on 2008-11-10
OK, here goes.

First the details: 

I'm running a MSI Wind Notebook that came with Windows XP. I've partitioned the drive and installed ubnuntu 8.10 - with no problems except for the modem. The modem is a Realtek Semiconductor Co., Ltd. RTL8187SE Wireless.

Now for the installation of the Realtek driver...

**Step 1:**

> ~$ wget [http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz](http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz)
--2008-11-10 15:33:44--  [http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz](http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz)
Resolving launchpadlibrarian.net... xx.xxx.xx.xxx
Connecting to launchpadlibrarian.net|xx.xxx.xx.xxx|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1977825 (1.9M) [application/x-tar]
Saving to: `rtl8187se_linux_26.1023.0928.2008.tar.gz.1'

100%[======================================>] 1,977,825    821K/s   in 2.4s    

2008-11-10 15:33:47 (821 KB/s) - `rtl8187se_linux_26.1023.0928.2008.tar.gz.1' saved [1977825/1977825]

**Step 2:**

I used the file browser to extract all the files to my home/michael folder.

**Step 3:**

I changed to the new directory.

**Step 4:**

Lots of stuff happened.
> 
$ ./makedrv
rm -f *.mod.c *.mod *.o .*.cmd *.ko  *~
rm -rf /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/tmp
make -C /lib/modules/2.6.27-7-generic/build M=/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/dot11d.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/dot11d.h:4,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/dot11d.c:11:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac.c:17:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_complete&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac.c:1969: warning: array subscript is above array bounds
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_rx.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_rx.c:46:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_tx.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_tx.c:56:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_wx.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_wx.c:37:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_wx.c: In function &#8216;ieee80211_wx_set_encode_ext&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_wx.c:670: warning: format not a string literal and no format arguments
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_module.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_module.c:55:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac_wx.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_softmac_wx.c:17:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt.c:26:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_ccmp.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_ccmp.c:25:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_tkip.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_tkip.c:24:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_wep.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_wep.c:21:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211-rtl.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211-rtl.ko
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/tmp
make -C /lib/modules/2.6.27-7-generic/build M=/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_core.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_core.c:67:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_sa2400.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_sa2400.c:26:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_93cx6.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_93cx6.h:16,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_93cx6.c:21:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_wx.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_wx.c:21:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_wx.c: At top level:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_wx.c:1386: warning: initialization from incompatible pointer type
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_wx.c:1388: warning: initialization from incompatible pointer type
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_max2820.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_max2820.c:28:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_gct.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_gct.c:28:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225.h:13,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225.c:16:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8255.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8255.c:16:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225z2.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225.h:13,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_rtl8225z2.c:14:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8185b_init.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8185b_init.c:24:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_dm.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_dm.h:4,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_dm.c:2:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  CC [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_pm.o
In file included from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.h:44,
                 from /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180_pm.c:17:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/ieee80211.h:1489: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.mod.o
  LD [M]  /home/michael/rtl8187se_linux_26.1023.0928.2008/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
michael@michael-laptop:~/rtl8187se_linux_26.1023.0928.2008$ 

**Step 5:**

> $ sudo ./wlan0up
[sudo] password for michael: 
michael@michael-laptop:~/rtl8187se_linux_26.1023.0928.2008$ 


**Finally 2 things:**

First, I can see the "Connect to Hidden Wireless Network" and the "New Wireless Network" but when I enter the coordinates for my router, I get a message saying that authentication is required. I notice that each time I enter my password, it is rejected and replaced with another random set of letters and numbers. Weird!

Second, When I turn my computer off, all the wireless settings disappear.


That's where it stands at the moment.

Cheers,

Michael

---

### Post by jepong on 2008-11-10
I have a msi wind. try this...

---

### Post by mckelly46 on 2008-11-11
Perfect driver solution jepong.

Now I only wish I could get me wireless to connect.

I installed 8.10 on my Acer TravelMate 8104WLMi and it has no problems at all connecting to my wireless router.

My MSI Wind is another story though.

I ping the router and its there, but I keep getting a message saying:

> Authentication required by wireless network
Passwords or encryption keys are required to access the wireless network 'linksys_SES_40327

I am using WPA Personal as my wireless security mode.

I noticed that the password on my Acer Laptop and the MSI Wind are the same - but they are both different from the password I set in my WPA Shared Key. So here's the mystery. Why does my Acer laptop log in automatically and with no problems, but the MSI does not?

Weird.

---

### Post by Rikki123s on 2008-12-07
i have the advent 4213 (the ECS G10iL). reading some forums from various websites, they say that it also includes the realtek RTL8187SE. would this driver work on the 4213?

---

