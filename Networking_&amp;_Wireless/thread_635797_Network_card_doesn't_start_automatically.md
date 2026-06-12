---
title: "Network card doesn't start automatically"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-12-09
Hi.

I have a Realtek 8185 wireless card that I have installed with Ndiswrapper, however, although I can get it to work it will not start on boot until I enter:-

```
sudo /etc/init.d/networking restart
```

Why does this card not automatically start on boot?

---

### Post by Original Brownster on 2007-12-09
Hi,
I'll take a poke at this, I am thinking that the ndiswrapper module is not loading before the network starts, try adding it to the /etc/modules  file which contains a list of modules you want loaded at boot time.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
sbp2
ndiswrapper
```

---

### Post by ushills on 2007-12-12
Hi 

I tried this and I am still having problems.

It appears that initially the wireless card is loaded as wlan0, then ndiswrapper changes this to wlan1 for some reason.

As this happens after the networking interfaces have been loaded networking doesn't start automatically,   how can I fix this?

---

### Post by Original Brownster on 2007-12-12
Hi,
Very strange assuming you only have 1 wireless device. 
I suspect a kernel driver for this device maybe loading, check the output of
$ sudo lshw -C network

look to see if it lists 2 wireless interfaces and which module/ driver it's loading. If it is loading a kernel module, blacklist it in /etc/modprobe.d/blacklist

if no success post the above output and also

$ iwconfig

---

### Post by ushills on 2007-12-12
Thanks I will try that, also only have one wireless card and this changes between wlan0 and wlan1.

---

