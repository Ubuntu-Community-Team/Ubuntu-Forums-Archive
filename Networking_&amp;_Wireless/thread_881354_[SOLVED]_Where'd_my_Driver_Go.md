---
title: "[SOLVED] Where'd my Driver Go?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by xchecker on 2008-08-05
We have a new box running Heron 8.04 and have connected successfully to my Linksys router using a WUSB54G v4 wireless adapter, but the connection slows down at times or drops completely.  Later it reappears seemingly by itself.  Today I've had no connection at all, although my Windows PC wired directly to the router is fine.  When I run the lshw -C Network command I notice that no driver is shown.  I could have sworn I have been using the rtb2500usb driver, but where is it now?

*-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:72:e9:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g

Is this a clue to the problem and if so, how do I fix it?

---

### Post by anubhavrocks on 2008-08-05
Can you also post the output of
```
dmesg
```

---

### Post by xchecker on 2008-08-05
Thanks for replying so promptly.  Here is the tail end of that command.  If you need another part please let me know; it's very long.

```

[   63.880719] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   63.881078] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   75.282538] NET: Registered protocol family 17 
[   76.402702] wlan0: Initial auth_alg=0 
[   76.402711] wlan0: authenticate with AP 00:14:bf:16:fc:66 
[   76.406756] wlan0: RX authentication from 00:14:bf:16:fc:66 (alg=0 transaction=2 status=0) 
[   76.406765] wlan0: authenticated 
[   76.406767] wlan0: associate with AP 00:14:bf:16:fc:66 
[   76.410949] wlan0: RX AssocResp from 00:14:bf:16:fc:66 (capab=0x401 status=0 aid=1) 
[   76.410953] wlan0: associated 
[   76.410958] wlan0: switched to short barker preamble (BSSID=00:14:bf:16:fc:66) 
[   76.414057] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   86.820308] wlan0: no IPv6 routers present 
[  118.793717] wlan0: deauthenticate(reason=3) 
[  902.245680] wlan0: Initial auth_alg=0 
[  902.245686] wlan0: authenticate with AP 00:14:bf:16:fc:66 
[  902.247723] wlan0: RX authentication from 00:14:bf:16:fc:66 (alg=0 transaction=2 status=0) 
[  902.247728] wlan0: authenticated 
[  902.247732] wlan0: associate with AP 00:14:bf:16:fc:66 
[  902.250097] wlan0: RX AssocResp from 00:14:bf:16:fc:66 (capab=0x401 status=0 aid=1) 
[  902.250103] wlan0: associated 
[  902.250109] wlan0: switched to short barker preamble (BSSID=00:14:bf:16:fc:66) 
[  902.252855] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[  912.682094] wlan0: no IPv6 routers present 
[  946.241250] wlan0: deauthenticate(reason=3) 
[ 7620.598874] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 7644.765586] wlan0: Initial auth_alg=0 
[ 7644.765592] wlan0: authenticate with AP 00:14:bf:16:fc:66 
[ 7644.768032] wlan0: RX authentication from 00:14:bf:16:fc:66 (alg=0 transaction=2 status=0) 
[ 7644.768038] wlan0: authenticated 
[ 7644.768043] wlan0: associate with AP 00:14:bf:16:fc:66 
[ 7644.770396] wlan0: RX AssocResp from 00:14:bf:16:fc:66 (capab=0x401 status=0 aid=1) 
[ 7644.770401] wlan0: associated 
[ 7644.770407] wlan0: switched to short barker preamble (BSSID=00:14:bf:16:fc:66) 
[ 7644.773160] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 7655.574766] wlan0: no IPv6 routers present 
[ 7772.947955] wlan0: Initial auth_alg=0 
[ 7772.947963] wlan0: authenticate with AP 00:14:bf:16:fc:66 
[ 7772.950305] wlan0: RX authentication from 00:14:bf:16:fc:66 (alg=0 transaction=2 status=0) 
[ 7772.950310] wlan0: authenticated 
[ 7772.950315] wlan0: associate with AP 00:14:bf:16:fc:66 
[ 7772.952674] wlan0: RX AssocResp from 00:14:bf:16:fc:66 (capab=0x401 status=0 aid=1) 
[ 7772.952679] wlan0: associated 
[ 7772.962484] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 7783.803966] wlan0: no IPv6 routers present 
[ 7819.868759] wlan0: deauthenticate(reason=3) 

```

---

### Post by anubhavrocks on 2008-08-05
do you have ndiswrapper?

---

### Post by xchecker on 2008-08-05
Not installed, no.

---

### Post by anubhavrocks on 2008-08-05
you can also try this out:
[http://blog.eksfiles.net/2008/07/06/sucess-with-hardy-heron-and-linksys-wusb54g-wireless-adapter/](http://blog.eksfiles.net/2008/07/06/sucess-with-hardy-heron-and-linksys-wusb54g-wireless-adapter/)

---

### Post by xchecker on 2008-08-06
So I should go the ndiswrapper route?  Thanks for the link.  I will also look at

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

I was hoping to avoid doing that since the adapter worked out of the box, but since it isn't working anymore I guess I will dive in.
Thanks!

---

