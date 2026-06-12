---
title: "Can I download wpa-supplicant somewhere?"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by gohanssjn on 2008-06-10
My desktop has no connection in Ubuntu, only Vista.  So I need to be able to download that package in Vista and then run it.

This also means that I cannot grab things like build-essential.

Can i grab a .deb anywhere for this?

---

### Post by chili555 on 2008-06-10
Check here: [http://packages.ubuntu.com/hardy/i386/wpasupplicant/download](http://packages.ubuntu.com/hardy/i386/wpasupplicant/download)

---

### Post by gohanssjn on 2008-06-10
Ok, new issue:

Can I download the madwifi amd64 driver anywhere?

EDIT: Nevermind, found the package there.  hope it works!

---

### Post by gohanssjn on 2008-06-10
No go :(

---

### Post by chili555 on 2008-06-10
> No goWhat didn't go? Who didn't go? Why didn't they go? Do they not have enough money or gas to go? When will they be ready to go?

In other words, what didn't work, that we might help you with?> This also means that I cannot grab things like build-essential.*build-essential* is an empty package that has dependencies which are essential, mostly to compile from source. They are libc6-dev, libc-dev, gcc (version >= 4:4.1.1), g++ (version >= 4:4.1.1), make and dpkg-dev. The dev packages will depend on their namesakes, for example, dpkg-dev will depend on dpkg, and so forth.

---

### Post by gohanssjn on 2008-06-10
Well, whenever I try this network card, I get nothing.  At all.  i can get better details in a little while.

My last option that I can think of is to activate another driver.  i have been trying madwifi as people have suggested, but I swear Vista says it is using a Prism driver.

Should I try to wrap it somehow?

---

### Post by chili555 on 2008-06-10
Let's see what:```
sudo lshw -C network
```tells us we *really* have. Let's not guess.

Looking at your other posts, I suspect this might help: [http://nothingoutoftheordinary.com/2007/03/11/wg311v3-64-bit-driver/](http://nothingoutoftheordinary.com/2007/03/11/wg311v3-64-bit-driver/)

---

### Post by gohanssjn on 2008-06-10
Doing what you just posted now.  I tried the PRISM driver + ndiswrapper, but it won't wrap.

Here is the output:

****@****-*******:~/inf$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:**:**:**:**:**
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=0.0.0 latency=32 module=hostap_pci multicast=yes wireless=IEEE 802.11-DS

---

### Post by gohanssjn on 2008-06-10
Well, if we can;t find an answer, I bought a new wireless card tonight in anticipation.

Trying a blacklist fix really quick.  it' a fresh install, so nothing to lose by 15 min to install again >.>

---

### Post by gohanssjn on 2008-06-10
New effort: downloaded wpa_supplicant and used the WPA guide that is Stickied.  i get this on restart:

wifi0: unknown hardware address type 801
SIOCSIFFLAGS: Invalid argument
SIOCSIFFLAGS: Invalid argument
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down

Setting have been triple checked :(

---

### Post by gohanssjn on 2008-06-10
New test.

[http://ubuntuforums.org/showthread.php?t=454436](http://ubuntuforums.org/showthread.php?t=454436)

Still no connection.

---

### Post by gohanssjn on 2008-06-11
Well, I just decided to abandon ship and try the $40 Linksys WMP54G I got at CircuiCity today incase a solution could not be found.

Installed it and it recognized right away.

I lost hope when I found that D-Link did not release ANY 64 bit drivers for the card.

But if a solution can be found, please let me know, I'd love to get my $40 back...

---

### Post by gohanssjn on 2008-06-11
Well, giving up for now.

New card worked...but then my Xfi, nVidia (X got hosed), and TV Tuner cards had driver problems.  So no Ubuntu on the desktop for now, only the laptop I suppose...

---

