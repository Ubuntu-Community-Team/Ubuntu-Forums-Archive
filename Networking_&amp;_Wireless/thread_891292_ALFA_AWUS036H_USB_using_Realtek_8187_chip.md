---
title: "ALFA AWUS036H USB using Realtek 8187 chip"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by whoboo on 2008-08-15
According to the sourceforge wiki [http://rtl-wifi.sourceforge.net/wiki/Installing#Removing_mainline_ieee80211_Stack](http://rtl-wifi.sourceforge.net/wiki/Installing#Removing_mainline_ieee80211_Stack) 
NOTE : the rtl-wifi drivers are in recent kernels. rtl8180 is in mainline kernel since 2.6.23 and 2.6.25 is in mainline kernel since 2.6.25, so under these kernels you don't need to compile the driver if you only wants to make your wifi working. 

I have installed Hardy, hoping the wireless would work.  It doesn't.  It works great on XP though.

All suggestions welcomed, TIA.

---

### Post by whoboo on 2008-08-18
It did not seem the usb wireless device can be recognized by ubuntu if it is plugged into a Belkin hub.  It is recognized when plugged into a USB slot connected directly to the computer bus, though.

However, after installing ndiswrapper and installing the net8187b driver per [http://mycirilo.com/?p=24](http://mycirilo.com/?p=24) BUT WITHOUT THE MODIFICATION TO THE INF FILE CHANGING 8187 TO 8189,it seems the usb can be recognized when it is plugged into the Belkin hub.

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

Why does the driver under windows blink the adapter l.e.d., but not under linux ? To drive you crazy.  I do appreciate the feedback in the various logs though.

At this stage of the game, it's rather pathetic that you can't easily get wireless and winmodems to work under linux.

---

### Post by whoboo on 2008-08-18
That above was for the emachine desktop.  On the laptop, Compaq 2190US, neither the windows driver nor the kernel driver will work with the adapter.  The crap out is explained in the logs visible via System Log in the System > Administration menu.

This sucks.


Windows XP lights the l.e.d. and loads the adapter and connects.

---

### Post by whoboo on 2008-08-21
Realtek - Jason Chang <jasonchang@realtek.com>
Subject: Re: driver for alfa awuso36h usb adapter using realteck 8187
Date: Mon, 18 Aug 2008 15:55:16 +0800

Dear Sir,
Thanks for your e-mail.
Please download RTL8187L Linux driver by following URL.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)
Description: Linux driver for kernel 2.6.X
----------------------------------
Maybe, this will work.

---

### Post by rashwan on 2008-09-13
> **whoboo said:**
> Realtek - Jason Chang <jasonchang@realtek.com>
Subject: Re: driver for alfa awuso36h usb adapter using realteck 8187
Date: Mon, 18 Aug 2008 15:55:16 +0800

Dear Sir,
Thanks for your e-mail.
Please download RTL8187L Linux driver by following URL.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)
Description: Linux driver for kernel 2.6.X
----------------------------------
Maybe, this will work.

actually it doesn't

---

### Post by god=none on 2008-11-22
The rtl8187 driver has been working here. I've used it with the AWUS036H in 2.6.24 and 2.6.26 kernels using Debian, Ubuntu and Damn Small Linux. The little LED doesn't flash but most times that is a desired feature to me.

This may have nothing to do with the Alpha or the rtl8187 driver but, it has been mentioned in other forums so I will just note that I've had occasional problems with web pages not loading after the connection has been up for a while. I've been working around that by resetting the connection. Also, at times everything works great for an extended time (several hours or more). If the problem was with the AWUS036H or the rtl8187 driver shouldn't the problem be observed more consistently?

I'm rather happy with the Alpha AWUS036H and the rtl8187 driver, thank you very much.

---

### Post by alcapone-g on 2008-12-07
The link [http://www.realtek.com.tw/downloads/...=true#RTL8187L](http://www.realtek.com.tw/downloads/...=true#RTL8187L) has old drive that does not do anything good.
you can check my output from conslo:
mariusz@virus-1:~/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007$ sudo ./makedrv
[sudo] password for mariusz: 
ieee80211/
ieee80211/license
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_rx.c
ieee80211/tags
ieee80211/ieee80211_crypt_tkip.c
ieee80211/Makefile
ieee80211/readme
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211.h
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt.h
rtl8187/
rtl8187/license
rtl8187/r8180_rtl8225z2.c
rtl8187/r8180_rtl8225.h
rtl8187/r8187_led.c
rtl8187/r8180_93cx6.h
rtl8187/r8180_wx.h
rtl8187/r8180_hw.h
rtl8187/copying
rtl8187/r8187_led.h
rtl8187/r8180_pm.h
rtl8187/tags
rtl8187/r8187.h
rtl8187/Makefile
rtl8187/r8180_rtl8225.c
rtl8187/readme
rtl8187/install
rtl8187/.tmp_versions/
rtl8187/.tmp_versions/r8187.mod
rtl8187/changes
rtl8187/r8180_wx.c
rtl8187/r8180_pm.c
rtl8187/r8187_core.c
rtl8187/r8180_93cx6.c
rtl8187/authors
rtl8187/ieee80211.h
rtl8187/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/tmp
make -C /lib/modules/2.6.27-9-generic/build M=/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o
In file included from /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:17:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211.h:1212: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:421: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:495: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:915: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol_rtl&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2120: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: (Each undeclared identifier is reported only once
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: for each function it appears in.)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2230:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2231:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2232:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2233:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2234:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2255: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
make[2]: *** [/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/tmp
make -C /lib/modules/2.6.27-9-generic/build M=/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o
In file included from /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:64:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:48:27: error: asm/semaphore.h: No such file or directory
In file included from /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:50,
                 from /home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:64:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/ieee80211.h:1212: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: (Each undeclared identifier is reported only once
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: for each function it appears in.)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_remove&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:456: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_rx_urbsubmit&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:730: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:1648: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_init&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_probe&#8217;:
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2938: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2956: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
make[2]: *** [/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/mariusz/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
mariusz@virus-1:~/ExtraUbuntu/rtl8187_linux_26.1025.0328.2007$

---

### Post by jdice on 2010-07-07
For those of you who have this same problem or any other problem related to your wireless connection, make sure to download file RTL8187L from realtek.com. This should solve any connection problems you may have.

---

