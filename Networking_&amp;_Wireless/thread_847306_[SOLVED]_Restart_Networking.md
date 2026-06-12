---
title: "[SOLVED] Restart Networking"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Brendon Rogers on 2008-07-02
Ubuntu 8.04 x64 Server
Belkin 54G USB wifi adapter

Each time I restart the server I initially don't have any network connectivity. I must manually restart the network:
[COLOR="Blue"]/etc/init.d/networking restart[/COLOR]

then everything works fine.

I am not sure where to start looking for the problem. Any suggestions gladly accepted.

TIA

Brendon

---

### Post by pytheas22 on 2008-07-02
A good place to start is the output of dmesg.  It will probably contain information about what's wrong.

If not, have you tried to narrow down the problem?  For instance, what if you just ifdown and ifup the interface (does an interface exist to begin with before restarting networking?), does that solve the problem?  Or reload the module?  Try to figure out which specific part of networking needs to be restarted so that you know where exactly the problem lies.

Otherwise, you could easily work around this whole problem by writing a script to restart networking right after boot.  But it would probably be better to track down the real problem.

---

### Post by Brendon Rogers on 2008-07-03
Thanks for the reply.

After a reboot dmesg shows:

[COLOR="RoyalBlue"][   73.074353] ieee80211_crypt: registered algorithm 'NULL'
[   73.112591] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   73.112596] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   73.282522] usb 2-7: reset high speed USB device using ehci_hcd and address 4
[   73.442701] zd1211rw 2-7:1.0: eth2
[   73.442719] usbcore: registered new interface driver zd1211rw
[   74.413659] zd1211rw 2-7:1.0: firmware version 4725
[   74.453706] zd1211rw 2-7:1.0: zd1211b chip 050d:705c v4810 high 00-1c-df AL2230_RF pa0 g--NS
[   74.618761] NET: Registered protocol family 17
[   74.977928] loop: module loaded
[   75.084649] lp: driver loaded but no devices found
[   75.568739] NET: Registered protocol family 10
[   75.568984] lo: Disabled Privacy Extensions
[   75.569752] ADDRCONF(NETDEV_UP): eth2: link is not ready[/COLOR]


eth2 is my wlan card, eth0 and eth1 are on board wired nics which I am not using.

I can ping the static IP address of eth2 from the server itself.

eth2 shows as being up after reboot

iwconfig shows eth2 with Access Point: Invalid

If I ifdown then ifup eth2 then full networking functionality is restored and I see the following in dmesg:

[COLOR="RoyalBlue"][  347.445917] ADDRCONF(NETDEV_UP): eth2: link is not ready
[  347.629404] SoftMAC: Open Authentication completed with 00:16:9c:ab:07:90
[  347.638496] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[  347.649589] ieee80211_crypt: registered algorithm 'TKIP'
[  352.279044] eth2: no IPv6 routers present[/COLOR]

I have tried adding 
/etc/init.d/networking restart
and
ifdown eth2
ifup eth2

to /etc/rc.local

but this doesn't help

My wifi nic is a Belkin F5D7050 v.4 which is listed on [http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices) as being compatible with the zd1211rw driver.

---

### Post by lisati on 2008-07-03
Although addressing network problems in a slightly different context, [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2) *might* be of help.

---

### Post by Brendon Rogers on 2008-07-03
Thanks Lisati for the link.

I sym linked the script to S54 and my network now starts properly after a reboot.

---

