---
title: "Ndiswrapper 1.51 problems with BCM4321AG"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Ian Milligan on 2007-12-19
hey, using ndiswrapper 1.51 and a BCM4321AG with 32bit XP drivers grabbed from the HP website for the dv9000-CTO, I've noticed generally good performance, but it occasionally disconnects.  Oddly enough it only seems to disconnect while using a package manager (which I attribute to the high bandwidth, although it seems odd, it's never during regular internet use).  I know its therefore an ndiswrapper issue not strictly a distribution issue, but I was hoping someone here would know what's up.  Here's the end of my dmesg:

eth1: no link during initialization.
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth1: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
NET: Registered protocol family 17
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present
ndiswrapper (iw_set_freq:334): setting configuration failed (00010003)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present
ndiswrapper (iw_set_freq:334): setting configuration failed (00010003)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present

I hope that makes sense to someone.
I'm using Hardy Heron, and 2.6.23.12 custom kernel, although I had this problem for a while before switching kernels.  Anyways, I suspect others may be having this problem, when I get around to it I'll try different ndiswrapper versions and see if I can replicate this problem, and post my results here just in case.

edit: this is after a couple d/c's
edit: also disconnecting from the wireless network and reconnecting fixes the problem, no need to reload ndiswrapper.

---

### Post by buzzbo on 2008-02-11
I realize this thread is months ago, but it came up on a search, among other things.

My computer has similar problems, when I close the lid, or when it sits for awhile, and the wireless disconnects and I get the following from dmesg:
[COLOR="Red"]
[16607.019163] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)[/COLOR]

And, so I found some info regarding blacklisting, so I did the following:

```
sudo vim /etc/modprobe.d/blacklist
``` (or substitute your favorite editor), and comment out the following line:

[COLOR="Red"]blacklist bcm43xx[/COLOR]
so it reads:
[COLOR="Red"]# blacklist bcm43xx[/COLOR]

then I unloaded and reloaded the ndiswrapper module from/to the kernel:
```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

And my wifi came right back  However, I am not sure if it is directly related to unblacklisting the bcm43xx driver, or just unloading and reloading ndiswrapper. :) This has been a problem for quite awhile, so I will report back as to long-term success.

Buzz

---

### Post by goldrake67 on 2008-04-30
i have the same problem with my ndiswrappered wifi card (inprocomm ipn 2220), but with kernel 2.6.22.14 it works fine and with kernel 2.6.24.16 it doesn't work. I have the same messages in the syslog but my connaissance don't allow me to solve this problem. If anyone can help us I will thank much.
Please, pardon my english but I'm italian and I don't often write in english

Regards

Goldrake

---

