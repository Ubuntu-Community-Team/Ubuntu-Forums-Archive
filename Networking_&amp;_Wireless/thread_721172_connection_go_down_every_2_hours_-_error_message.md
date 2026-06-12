---
title: "connection go down every 2 hours - error message"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by il-mArCi0 on 2008-03-11
hi guys
i get connected to internet by a wireless usb key and wicd software.
every 2-3 hours my connection go down and i must reboot my computer to go back on internet.
from the terminal i've got this error message

```
silvio@silvio-laptop:~$ tail -30 /var/log/messages
Mar 10 19:39:59 silvio-laptop pppd[5792]: remote IP address 192.168.100.1
Mar 10 19:39:59 silvio-laptop pppd[5792]: primary   DNS address 85.37.17.8
Mar 10 19:39:59 silvio-laptop pppd[5792]: secondary DNS address 85.38.28.73
Mar 10 19:39:59 silvio-laptop kernel: [ 2205.884000] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 10 20:03:55 silvio-laptop -- MARK --
Mar 10 20:23:55 silvio-laptop -- MARK --
Mar 10 20:43:55 silvio-laptop -- MARK --
Mar 10 21:03:56 silvio-laptop -- MARK --
Mar 10 21:23:57 silvio-laptop -- MARK --
Mar 10 21:34:08 silvio-laptop kernel: [ 9054.560000] usb 4-3: USB disconnect, address 3
Mar 10 21:36:38 silvio-laptop pppd[5792]: No response to 4 echo-requests
Mar 10 21:36:38 silvio-laptop pppd[5792]: Serial link appears to be disconnected.
Mar 10 21:36:38 silvio-laptop pppd[5792]: Connect time 116.7 minutes.
Mar 10 21:36:38 silvio-laptop pppd[5792]: Sent 1663203 bytes, received 6041607 bytes.
Mar 10 21:36:38 silvio-laptop pppd[5792]: restoring old default route to eth1 [192.168.1.1]
Mar 10 21:36:44 silvio-laptop pppd[5792]: Connection terminated.
Mar 10 21:36:44 silvio-laptop pppd[5792]: Modem hangup
Mar 10 21:37:49 silvio-laptop pppd[5792]: Timeout waiting for PADO packets
```

any suggestion?

---

### Post by SpaceTeddy on 2008-03-11
> **il-mArCi0 said:**
> 
```
Mar 10 21:34:08 silvio-laptop kernel: [ 9054.560000] usb 4-3: USB disconnect, address 3
```


your usb-modem is (somehow) turning itself off. Why i do not know - but this does not look like a network fault, but either a driver problem or a hardware failure.
sorry i can't be of any more help - i know pretty much nothing about usb :(

---

### Post by Jethro_uk on 2008-03-11
have no idea, but your problem sounds similar to mine (although I've not yet had a look at any logs).

USB wireless, configured with wiCD, works fine for a few hours, then seems to freeze, but works immediately after reboot.

I wonder if it's a stack overflowing somewhere ....

---

### Post by SpaceTeddy on 2008-03-11
right after this happens, maybe you should take a look at the kernel log to see if anything happened there that shut down the modem

you can do this via 
```
dmesg |tail
```

---

### Post by il-mArCi0 on 2008-03-13
> **SpaceTeddy said:**
> right after this happens, maybe you should take a look at the kernel log to see if anything happened there that shut down the modem

you can do this via 
```
dmesg |tail
```

i got this error```


[ 3031.168000] usb 4-3: USB disconnect, address 3
[ 3031.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
[ 3032.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
[ 3033.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
[ 3034.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
[ 3035.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
[ 3036.896000] zd1211rw 4-3:1.0: zd_chip_control_leds error -19
```

---

### Post by SpaceTeddy on 2008-03-13
the error can be found on the net, yet there seems to be no solution i can make sense of (most replies arein french or italian, and babelfish is not that good at translating :( )... so unforteunatly, i cannot help you anymore. 

I know less than nothing about driver works :(

---

### Post by darrylmcginnis on 2008-03-13
This is a known issue that is quite common and occurs much too often!
You can track the status of this bug at:
[https://bugs.launchpad.net/bugs/74362]("https://bugs.launchpad.net/bugs/74362")

---

### Post by il-mArCi0 on 2008-03-14
> **darrylmcginnis said:**
> This is a known issue that is quite common and occurs much too often!
You can track the status of this bug at:
[https://bugs.launchpad.net/bugs/74362]("https://bugs.launchpad.net/bugs/74362")

thanks man!

---

