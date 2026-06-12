---
title: "Does a Qualcomm Atheros [168c:0042] /QCA9377/ath10k support monitor mode?"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by metro2 on 2016-03-21
Hi there!
I'm using Ubuntu 15.10 and the drivers for the wifi device has been already installed using this and other threads:
[http://ubuntuforums.org/showthread.php?t=2304250](http://ubuntuforums.org/showthread.php?t=2304250)

My Wlan is running but if I want to change the interface mode from managed to monitor I get this response:

```

# ifconfig wlan0 down
# iwconfig wlan0 mode monitor
# ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable

```

My Laptop Model: Acer ef 574g
wifi device: Qualcomm Atheros [168c:0042] /QCA9377 (NFA435)

What do you think? Maybe my wifi device doesn't support the monitor mode or it isn't implemented in the drivers?

---

### Post by chili555 on 2016-03-22
You can find out with:```
iw list
```My Intel card says:```
Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * [COLOR="#FF0000"]monitor[/COLOR]
		 * P2P-client
		 * P2P-GO
		 * P2P-device

```

---

### Post by jeremy31 on 2016-03-22
In addition to chili's request, post ```
iwconfig
```

---

### Post by metro2 on 2016-03-22
Thanks for the command. Didn't know it.

So iw says:
```

    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         [COLOR=#ff0000]* monitor[/COLOR]
         * mesh point
         * P2P-client
         * P2P-GO
         * P2P-device

```

So it is "supported", but it doesn't work. Maybe the kernel implementation isn't correct? If I use my usb wifi stick the monitor mode is working(for the stick not for my real card). So I don't think the way I change the mode is wrong or is there a better way? I tried it with airmon-ng too, but it doesn't work.

---

### Post by jeremy31 on 2016-03-22
Post the result of ```
iwconfig
``` as I doubt wlan0 is being used

---

### Post by metro2 on 2016-03-22
Ah, sorry guys. I'm using two distributions: kali and ubuntu. The problem happened with the kali kernel and the older ubuntu wifi drivers. After I updated it under Ubuntu, I tested it only with Kali and not Ubuntu... Now it's working. ](*,)
Never change a running distro ;)

Thanks anyway! And for your quick responses. After all I learned a new command.

---

