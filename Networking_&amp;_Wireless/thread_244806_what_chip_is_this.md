---
title: "what chip is this?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by gary800 on 2006-08-26
**Problem:** My Asus A4k notebook has an on-board wifi chip that not working. I want to check what features the chip has (WPA,WEP....) and make sure I load the right drivers.

Unfortunately, for the life of me, I cannot find out what make/manufacture of  the chip is.

**Info:**

dmesg

```
[17180718.228000] zd1205: (exit) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2417
[17180724.236000] STA_ASSOCIATED
[17180724.236000] mac addr = 00:14:6c:46:c6:b4
[17180728.836000] wlan0: no IPv6 routers present
[17181227.784000] zd1205: (enter) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2670
[17181227.904000] zd1205: (exit) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2696
[17181232.800000] zd1205: (enter) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2363
[17181232.800000] zd1205: (exit) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2417
[17181232.804000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17181233.308000] STA_ASSOCIATED
[17181233.308000] mac addr = 00:14:6c:46:c6:b4
[17182497.084000] zd1205: cmd = 8b14
[17182583.248000] zd1205: cmd = 8b03
[17182583.248000] zd1205: cmd = 8b09
[17182583.248000] zd1205: cmd = 8b1d
[17182583.248000] zd1205: cmd = 8b27
[17182583.256000] zd1205: cmd = 8b03
[17182583.260000] zd1205: cmd = 8b09
[17182583.260000] zd1205: cmd = 8b1d
[17182583.260000] zd1205: cmd = 8b27
[17182583.268000] zd1205: cmd = 8b03
[17182583.268000] zd1205: cmd = 8b09
[17182583.268000] zd1205: cmd = 8b1d
[17182583.268000] zd1205: cmd = 8b27
[17182583.276000] zd1205: cmd = 8b03
[17182583.276000] zd1205: cmd = 8b09
[17182583.276000] zd1205: cmd = 8b1d
[17182583.276000] zd1205: cmd = 8b27
[17182583.348000] zd1205: cmd = 8b03
[17182583.348000] zd1205: cmd = 8b09
[17182583.348000] zd1205: cmd = 8b1d
[17182583.348000] zd1205: cmd = 8b27
[17182583.380000] zd1205: cmd = 8b03
[17182583.380000] zd1205: cmd = 8b09
[17182583.380000] zd1205: cmd = 8b1d
[17182583.380000] zd1205: cmd = 8b27
[17182583.412000] zd1205: cmd = 8b03
[17182583.412000] zd1205: cmd = 8b09
[17182583.412000] zd1205: cmd = 8b1d
[17182583.412000] zd1205: cmd = 8b27
[17182583.420000] zd1205: cmd = 8b03
[17182583.420000] zd1205: cmd = 8b09
[17182583.420000] zd1205: cmd = 8b1d
[17182583.420000] zd1205: cmd = 8b27
[17182583.432000] zd1205: cmd = 8b03
[17182583.432000] zd1205: cmd = 8b09
[17182583.432000] zd1205: cmd = 8b1d
[17182583.432000] zd1205: cmd = 8b27
[17182583.440000] zd1205: cmd = 8b03
[17182583.440000] zd1205: cmd = 8b09
[17182583.440000] zd1205: cmd = 8b1d
[17182583.440000] zd1205: cmd = 8b27
[17182583.448000] zd1205: cmd = 8b03
[17182583.448000] zd1205: cmd = 8b09
[17182583.448000] zd1205: cmd = 8b1d
[17182583.448000] zd1205: cmd = 8b27
[17182583.460000] zd1205: cmd = 8b03
[17182583.460000] zd1205: cmd = 8b09
[17182583.460000] zd1205: cmd = 8b1d
[17182583.460000] zd1205: cmd = 8b27
[17182583.468000] zd1205: cmd = 8b03
[17182583.468000] zd1205: cmd = 8b09
[17182583.468000] zd1205: cmd = 8b1d
[17182583.468000] zd1205: cmd = 8b27
[17182583.476000] zd1205: cmd = 8b03
[17182583.476000] zd1205: cmd = 8b09
[17182583.480000] zd1205: cmd = 8b1d
[17182583.480000] zd1205: cmd = 8b27
[17182583.488000] zd1205: cmd = 8b03
[17182583.488000] zd1205: cmd = 8b09
[17182583.488000] zd1205: cmd = 8b1d
[17182583.488000] zd1205: cmd = 8b27
[17182583.496000] zd1205: cmd = 8b03
[17182583.496000] zd1205: cmd = 8b09
[17182583.496000] zd1205: cmd = 8b1d
[17182583.496000] zd1205: cmd = 8b27
[17182583.504000] zd1205: cmd = 8b03
[17182583.504000] zd1205: cmd = 8b09
[17182583.504000] zd1205: cmd = 8b1d
[17182583.504000] zd1205: cmd = 8b27
[17182583.516000] zd1205: cmd = 8b03
[17182583.516000] zd1205: cmd = 8b09
[17182583.516000] zd1205: cmd = 8b1d
[17182583.516000] zd1205: cmd = 8b27
[17182583.524000] zd1205: cmd = 8b03
[17182583.524000] zd1205: cmd = 8b09
[17182583.524000] zd1205: cmd = 8b1d
[17182583.524000] zd1205: cmd = 8b27
[17182583.532000] zd1205: cmd = 8b03
[17182583.532000] zd1205: cmd = 8b09
[17182583.532000] zd1205: cmd = 8b1d
[17182583.532000] zd1205: cmd = 8b27
[17182583.544000] zd1205: cmd = 8b03
[17182583.544000] zd1205: cmd = 8b09
[17182583.544000] zd1205: cmd = 8b1d
[17182583.544000] zd1205: cmd = 8b27
[17182583.552000] zd1205: cmd = 8b03
[17182583.552000] zd1205: cmd = 8b09
[17182583.552000] zd1205: cmd = 8b1d
[17182583.552000] zd1205: cmd = 8b27
[17182583.564000] zd1205: cmd = 8b03
[17182583.564000] zd1205: cmd = 8b09
[17182583.564000] zd1205: cmd = 8b1d
[17182583.564000] zd1205: cmd = 8b27
[17182583.576000] zd1205: cmd = 8b03
[17182583.576000] zd1205: cmd = 8b09
[17182583.576000] zd1205: cmd = 8b1d
[17182583.576000] zd1205: cmd = 8b27
[17182583.588000] zd1205: cmd = 8b03
[17182583.588000] zd1205: cmd = 8b09
[17182583.588000] zd1205: cmd = 8b1d
[17182583.588000] zd1205: cmd = 8b27
[17182583.596000] zd1205: cmd = 8b03
[17182583.596000] zd1205: cmd = 8b09
[17182583.596000] zd1205: cmd = 8b1d
[17182583.596000] zd1205: cmd = 8b27
[17182583.604000] zd1205: cmd = 8b03
[17182583.604000] zd1205: cmd = 8b09
[17182583.604000] zd1205: cmd = 8b1d
[17182583.604000] zd1205: cmd = 8b27
[17182583.640000] zd1205: cmd = 8b03
[17182583.640000] zd1205: cmd = 8b09
[17182583.640000] zd1205: cmd = 8b1d
[17182583.640000] zd1205: cmd = 8b27
[17182622.440000] zd1205: (enter) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2670
[17182622.652000] zd1205: (exit) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2696
[17182622.688000] zd1205: (enter) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2363
[17182622.692000] zd1205: (exit) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2417
[17182622.692000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17182623.212000] STA_ASSOCIATED
[17182623.212000] mac addr = 00:14:6c:46:c6:b4
[17182626.564000] zd1205: cmd = 8b03
[17182626.568000] zd1205: cmd = 8b09
[17182626.568000] zd1205: cmd = 8b1d
[17182626.568000] zd1205: cmd = 8b27
[17182626.776000] zd1205: cmd = 8b03
[17182626.776000] zd1205: cmd = 8b09
[17182626.776000] zd1205: cmd = 8b1d
[17182626.776000] zd1205: cmd = 8b27
[17182626.796000] zd1205: cmd = 8b03
[17182626.796000] zd1205: cmd = 8b09
[17182626.796000] zd1205: cmd = 8b1d
[17182626.796000] zd1205: cmd = 8b27
[17182626.816000] zd1205: cmd = 8b03
[17182626.816000] zd1205: cmd = 8b09
[17182626.816000] zd1205: cmd = 8b1d
[17182626.816000] zd1205: cmd = 8b27
[17182626.832000] zd1205: cmd = 8b03
[17182626.832000] zd1205: cmd = 8b09
[17182626.832000] zd1205: cmd = 8b1d
[17182626.832000] zd1205: cmd = 8b27
[17182626.852000] zd1205: cmd = 8b03
[17182626.852000] zd1205: cmd = 8b09
[17182626.852000] zd1205: cmd = 8b1d
[17182626.852000] zd1205: cmd = 8b27
[17182626.872000] zd1205: cmd = 8b03
[17182626.872000] zd1205: cmd = 8b09
[17182626.872000] zd1205: cmd = 8b1d
[17182626.872000] zd1205: cmd = 8b27
[17182626.896000] zd1205: cmd = 8b03
[17182626.896000] zd1205: cmd = 8b09
[17182626.896000] zd1205: cmd = 8b1d
[17182626.896000] zd1205: cmd = 8b27
[17182626.916000] zd1205: cmd = 8b03
[17182626.916000] zd1205: cmd = 8b09
[17182626.916000] zd1205: cmd = 8b1d
[17182626.916000] zd1205: cmd = 8b27
[17182626.936000] zd1205: cmd = 8b03
[17182626.936000] zd1205: cmd = 8b09
[17182626.936000] zd1205: cmd = 8b1d
[17182626.936000] zd1205: cmd = 8b27
[17182626.956000] zd1205: cmd = 8b03
[17182626.956000] zd1205: cmd = 8b09
[17182626.956000] zd1205: cmd = 8b1d
[17182626.956000] zd1205: cmd = 8b27
[17182626.972000] zd1205: cmd = 8b03
[17182626.976000] zd1205: cmd = 8b09
[17182626.976000] zd1205: cmd = 8b1d
[17182626.976000] zd1205: cmd = 8b27
[17182626.992000] zd1205: cmd = 8b03
[17182626.992000] zd1205: cmd = 8b09
[17182626.992000] zd1205: cmd = 8b1d
[17182626.992000] zd1205: cmd = 8b27
[17182627.012000] zd1205: cmd = 8b03
[17182627.012000] zd1205: cmd = 8b09
[17182627.012000] zd1205: cmd = 8b1d
[17182627.012000] zd1205: cmd = 8b27
[17182627.032000] zd1205: cmd = 8b03
[17182627.032000] zd1205: cmd = 8b09
[17182627.032000] zd1205: cmd = 8b1d
[17182627.032000] zd1205: cmd = 8b27
[17182627.052000] zd1205: cmd = 8b03
[17182627.052000] zd1205: cmd = 8b09
[17182627.052000] zd1205: cmd = 8b1d
[17182627.052000] zd1205: cmd = 8b27
[17182627.068000] zd1205: cmd = 8b03
[17182627.068000] zd1205: cmd = 8b09
[17182627.068000] zd1205: cmd = 8b1d
[17182627.068000] zd1205: cmd = 8b27
[17182627.088000] zd1205: cmd = 8b03
[17182627.088000] zd1205: cmd = 8b09
[17182627.088000] zd1205: cmd = 8b1d
[17182627.088000] zd1205: cmd = 8b27
[17182627.104000] zd1205: cmd = 8b03
[17182627.104000] zd1205: cmd = 8b09
[17182627.104000] zd1205: cmd = 8b1d
[17182627.104000] zd1205: cmd = 8b27
[17182627.124000] zd1205: cmd = 8b03
[17182627.124000] zd1205: cmd = 8b09
[17182627.124000] zd1205: cmd = 8b1d
[17182627.124000] zd1205: cmd = 8b27
[17182627.148000] zd1205: cmd = 8b03
[17182627.148000] zd1205: cmd = 8b09
[17182627.148000] zd1205: cmd = 8b1d
[17182627.148000] zd1205: cmd = 8b27
[17182627.164000] zd1205: cmd = 8b03
[17182627.164000] zd1205: cmd = 8b09
[17182627.168000] zd1205: cmd = 8b1d
[17182627.168000] zd1205: cmd = 8b27
[17182687.484000] zd1205: cmd = 8b03
[17182687.484000] zd1205: cmd = 8b09
[17182687.484000] zd1205: cmd = 8b1d
[17182687.484000] zd1205: cmd = 8b27
[17182687.496000] zd1205: cmd = 8b03
[17182687.496000] zd1205: cmd = 8b09
[17182687.496000] zd1205: cmd = 8b1d
[17182687.496000] zd1205: cmd = 8b27
[17182687.504000] zd1205: cmd = 8b03
[17182687.504000] zd1205: cmd = 8b09
[17182687.504000] zd1205: cmd = 8b1d
[17182687.504000] zd1205: cmd = 8b27
[17182687.512000] zd1205: cmd = 8b03
[17182687.512000] zd1205: cmd = 8b09
[17182687.512000] zd1205: cmd = 8b1d
[17182687.512000] zd1205: cmd = 8b27
[17182687.588000] zd1205: cmd = 8b03
[17182687.588000] zd1205: cmd = 8b09
[17182687.588000] zd1205: cmd = 8b1d
[17182687.588000] zd1205: cmd = 8b27
[17182687.624000] zd1205: cmd = 8b03
[17182687.624000] zd1205: cmd = 8b09
[17182687.624000] zd1205: cmd = 8b1d
[17182687.624000] zd1205: cmd = 8b27
[17182687.656000] zd1205: cmd = 8b03
[17182687.656000] zd1205: cmd = 8b09
[17182687.656000] zd1205: cmd = 8b1d
[17182687.656000] zd1205: cmd = 8b27
[17182687.664000] zd1205: cmd = 8b03
[17182687.664000] zd1205: cmd = 8b09
[17182687.664000] zd1205: cmd = 8b1d
[17182687.664000] zd1205: cmd = 8b27
[17182687.676000] zd1205: cmd = 8b03
[17182687.676000] zd1205: cmd = 8b09
[17182687.676000] zd1205: cmd = 8b1d
[17182687.676000] zd1205: cmd = 8b27
[17182687.688000] zd1205: cmd = 8b03
[17182687.688000] zd1205: cmd = 8b09
[17182687.688000] zd1205: cmd = 8b1d
[17182687.688000] zd1205: cmd = 8b27
[17182687.696000] zd1205: cmd = 8b03
[17182687.696000] zd1205: cmd = 8b09
[17182687.696000] zd1205: cmd = 8b1d
[17182687.696000] zd1205: cmd = 8b27
[17182687.704000] zd1205: cmd = 8b03
[17182687.704000] zd1205: cmd = 8b09
[17182687.704000] zd1205: cmd = 8b1d
[17182687.704000] zd1205: cmd = 8b27
[17182687.716000] zd1205: cmd = 8b03
[17182687.716000] zd1205: cmd = 8b09
[17182687.716000] zd1205: cmd = 8b1d
[17182687.716000] zd1205: cmd = 8b27
[17182687.724000] zd1205: cmd = 8b03
[17182687.724000] zd1205: cmd = 8b09
[17182687.724000] zd1205: cmd = 8b1d
[17182687.724000] zd1205: cmd = 8b27
[17182687.736000] zd1205: cmd = 8b03
[17182687.736000] zd1205: cmd = 8b09
[17182687.736000] zd1205: cmd = 8b1d
[17182687.736000] zd1205: cmd = 8b27
[17182687.744000] zd1205: cmd = 8b03
[17182687.744000] zd1205: cmd = 8b09
[17182687.744000] zd1205: cmd = 8b1d
[17182687.744000] zd1205: cmd = 8b27
[17182687.756000] zd1205: cmd = 8b03
[17182687.756000] zd1205: cmd = 8b09
[17182687.756000] zd1205: cmd = 8b1d
[17182687.756000] zd1205: cmd = 8b27
[17182687.768000] zd1205: cmd = 8b03
[17182687.768000] zd1205: cmd = 8b09
[17182687.768000] zd1205: cmd = 8b1d
[17182687.768000] zd1205: cmd = 8b27
[17182687.776000] zd1205: cmd = 8b03
[17182687.776000] zd1205: cmd = 8b09
[17182687.776000] zd1205: cmd = 8b1d
[17182687.776000] zd1205: cmd = 8b27
[17182687.788000] zd1205: cmd = 8b03
[17182687.788000] zd1205: cmd = 8b09
[17182687.788000] zd1205: cmd = 8b1d
[17182687.788000] zd1205: cmd = 8b27
[17182687.796000] zd1205: cmd = 8b03
[17182687.796000] zd1205: cmd = 8b09
[17182687.796000] zd1205: cmd = 8b1d
[17182687.796000] zd1205: cmd = 8b27
[17182687.808000] zd1205: cmd = 8b03
[17182687.808000] zd1205: cmd = 8b09
[17182687.808000] zd1205: cmd = 8b1d
[17182687.808000] zd1205: cmd = 8b27
[17182687.816000] zd1205: cmd = 8b03
[17182687.816000] zd1205: cmd = 8b09
[17182687.816000] zd1205: cmd = 8b1d
[17182687.816000] zd1205: cmd = 8b27
[17182687.828000] zd1205: cmd = 8b03
[17182687.828000] zd1205: cmd = 8b09
[17182687.828000] zd1205: cmd = 8b1d
[17182687.828000] zd1205: cmd = 8b27
[17182687.840000] zd1205: cmd = 8b03
[17182687.840000] zd1205: cmd = 8b09
[17182687.840000] zd1205: cmd = 8b1d
[17182687.840000] zd1205: cmd = 8b27
[17182687.848000] zd1205: cmd = 8b03
[17182687.848000] zd1205: cmd = 8b09
[17182687.848000] zd1205: cmd = 8b1d
[17182687.848000] zd1205: cmd = 8b27
[17182687.856000] zd1205: cmd = 8b03
[17182687.856000] zd1205: cmd = 8b09
[17182687.856000] zd1205: cmd = 8b1d
[17182687.856000] zd1205: cmd = 8b27
[17182687.896000] zd1205: cmd = 8b03
[17182687.896000] zd1205: cmd = 8b09
[17182687.896000] zd1205: cmd = 8b1d
[17182687.896000] zd1205: cmd = 8b27
[17182701.036000] zd1205: (enter) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2670
[17182701.116000] zd1205: (exit) zd1205_close, drivers/usb/net/zd1211/zd1205.c line 2696
[17182701.176000] zd1205: (enter) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2363
[17182701.180000] zd1205: (exit) zd1205_open, drivers/usb/net/zd1211/zd1205.c line 2417
[17182701.180000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17182701.712000] STA_ASSOCIATED
[17182701.712000] mac addr = 00:14:6c:46:c6:b4
[17185319.072000] Wait Rx Frames Length Info!!
[17185319.072000] Got Rx Frames Length Info!!
[17187144.720000] skge eth0: enabling interface
[17187144.724000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17187146.400000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[17187146.400000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17187156.456000] eth0: no IPv6 routers present
[17187159.944000] ohci_hcd 0000:00:02.1: wakeup
[17187160.328000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[17187160.700000] usbcore: registered new driver hiddev
[17187160.708000] input: Microsoft Basic Optical Mouse as /class/input/input3
[17187160.708000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:02.1-1
[17187160.708000] usbcore: registered new driver usbhid
[17187160.708000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17187171.140000] zd1205: cmd = 8b03
[17187171.140000] zd1205: cmd = 8b09
[17187171.140000] zd1205: cmd = 8b1d
[17187171.140000] zd1205: cmd = 8b27
[17187219.804000] pcmcia: Detected deprecated PCMCIA ioctl usage.
[17187219.804000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17187219.808000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[17187224.240000] zd1205: cmd = 8946
[17187224.240000] zd1205: cmd = 8946
[17187224.240000] zd1205: cmd = 8946
[17188374.616000] Switch to AP mode
[17188374.616000] Mixed Mode
[17188410.452000] zd1205: cmd = 8b03
[17188410.452000] zd1205: cmd = 8b09
[17188410.452000] zd1205: cmd = 8b1d
[17188410.452000] zd1205: cmd = 8b27
[17188435.384000] Switch to PSEUDO_IBSS mode
[17188435.384000] Mixed Mode
[17188436.056000] STA_ASSOCIATED
[17188436.056000] mac addr = 00:00:00:00:00:00
[17188439.772000] zd1205: cmd = 8b03
[17188439.772000] zd1205: cmd = 8b09
[17188439.772000] zd1205: cmd = 8b1d
[17188439.772000] zd1205: cmd = 8b27
[17188470.244000]  HashInsert macAddr =  data [6]:
[17188470.244000] 00 14 6c 46 c6 b4
```


iwconfig

```
root@carla-laptop:/home/carla# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"HAIG"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=76/92  Signal level=37/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:183  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```



iwlist scan

```
root@carla-laptop:/home/carla# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:46:C6:B4
                    ESSID:"HAIG"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:88/92  Signal level=-241 dBm  Noise level=-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

sit0      Interface doesn't support scanning.
```


lspci
```
root@carla-laptop:/home/carla# lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev f6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:02:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
```


lsusb

```
lsusb
root@carla-laptop:/home/carla# lsusb
Bus 003 Device 002: ID 0b05:170c ASUSTek Computer, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 0000:0000
root@carla-laptop:/home/carla#
```

---

### Post by pyros on 2006-08-26
according to the user manual ([ftp://dlsvr02.asus.com/pub/ASUS/nb/A4D/e1703_a4dk_sw.pdf](ftp://dlsvr02.asus.com/pub/ASUS/nb/A4D/e1703_a4dk_sw.pdf))
It's an SiS chip of some kind. A call or email to asus tech support may be in order.

---

### Post by tturrisi on 2006-08-27
It's usb wifi adapter:
Your specs:
[http://www.asus.com/products4.aspx?modelmenu=2&model=346&l1=5&l2=74&l3=292](http://www.asus.com/products4.aspx?modelmenu=2&model=346&l1=5&l2=74&l3=292)
If dual booting, boot to windows, downlolad this program called SIW and get full system details:
[http://www.gtopala.com/about_siw.html](http://www.gtopala.com/about_siw.html)
The wifi should work with ndiswrapper.

---

### Post by gary800 on 2006-08-29
Cool.

Found out that it was the Asus WL-159g chip. It uses the zd1211, which I removed, download the new driver and installed. Bang, it works.

---

### Post by tturrisi on 2006-08-29
Sweet!  It's really nice when it goes 1-2-3.

---

