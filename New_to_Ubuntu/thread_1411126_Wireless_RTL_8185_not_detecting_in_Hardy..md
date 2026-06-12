---
title: "Wireless RTL 8185 not detecting in Hardy."
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Ammon Van Meter on 2010-02-19
Hello. I am trying to get my built-in wireless working on my laptop. Gateway MX 3228. The inf file installs, however the card's presence is not seen. In windows, I have to install the motherboard to see the wireless. Do I have to do this as well?

---

### Post by cariboo on 2010-02-20
Does you're wireless device show up when you type in a terminal:

```
lspci
```

If it does, you should be able to use the windows drivers and ndiswrapper to make your device work.

---

### Post by lkraemer on 2010-02-21
First you need to find out more about the Hardware installed in your
Gateway Laptop.

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lspci -nn
lspci -nn | grep Marvell
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig
tail /var/log/messages

```

If  your Ubuntu version is <= 9.04 use:
cat /etc/modprobe.d/blacklist

What is the Ubuntu version and are you using 32 or 64 Bits?

lk

---

