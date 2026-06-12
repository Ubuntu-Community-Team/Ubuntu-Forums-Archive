---
title: "Feisty crawls at boot when USB wireless dongle is connected"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by RKCole on 2007-04-19
Hello, everyone.

I just installed Feisty and I am very impressed and happy with it.  There is just one issue that I am having right now, and I am not sure if it is a bug or a configuration problem.

I use a Cnet CWD-854 Wireless-G USB Dongle (which uses the RaLink RT73 chipset) to access the Internet wirelessly via my Linksys WRT54G Wireless Broadband Router.  I do not have a problem with accessing the Internet (I actually have everything, including WPA2/PSK+AES, set up and I am writing this post from Feisty).

The issue that I am having is that when I boot into Ubuntu (I dual boot at the moment), the boot-up process crawls and then freezes at the end of booting, so I have to proceed with a hard shutdown.  I have tested this with the dongle disconnected and the system boots perfectly.

**Information Regarding the RT73 Driver**
I use the RT73 driver which I obtained/compiled from [this page]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") as I could not get anything working with the driver (rt73usb) that comes with Feisty (or previous versions of Ubuntu) by default.

Any help regarding this issue would be greatly appreciated.

Take care.

---

### Post by RKCole on 2007-04-19
Problem solved.

Apparently when Feisty loads with my device (and apparently others with the RaLink RT73 chipset) connected, three drivers are loaded simultaneously--rt73usb, rt2500, and rt2x00lib.  I found a similar situation by a poster [here]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3638&sid=7d99a915a86b946dd92413119229b206").    I just tested the solution mentioned in the mentioned post, and everything works fine.

What one must do is blacklist rt73usb, rt2570, and rt2x00lib.  To do this, go into a terminal and execute the following commands:

```

$ sudo su
Password: _
# echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
# echo "blacklist rt2570" >> /etc/modprobe.d/blacklist
# echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist
# exit
$ exit

```

Now everything works like a charm.

Take care, everyone.

---

