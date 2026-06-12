---
title: "Belkin F5D7050 USB wireless G adapter causing freezes"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by edwinw on 2008-07-31
I'm having a problem with a Belkin F5D7050 USB wireless adapter in Ubuntu 8.04 (Hardy Heron).  There are several versions of this adapter using different wireless chipsets, according to this page:

[http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)

I have version 4000 of the card, which should be working.  Actually, it mostly works, in that all I have to do is plug it in and the driver loads fine and the networks are visible.  I then connect to a network without any problems.  However, leaving the network on, my computer freezes/hangs, no keyboard or mouse input does anything, and I have to do a hard reboot.  This doesn't happen right way, usually it happens after a couple of hours, even if nothing is being done on the computer.  Here's the output showing that the driver is loaded:

```

lsmod | grep zd
zd1211rw               56964  0 
ieee80211softmac       30976  1 zd1211rw
ieee80211              35528  2 zd1211rw,ieee80211softmac
usbcore               146028  6 usb_storage,libusual,zd1211rw,ehci_hcd,ohci_hcd

```

So the zd1211rw driver provided on a default 8.04 install is indeed loaded.

I've looked at various log files as well, and the entries seem pretty innocuous, but it does seem that there are some messages right around the time of the freeze.  Here's the end of /var/log/kern.log:

```

Jul 31 09:08:32 desktop4 kernel: [   76.493679] NET: Registered protocol family 10
Jul 31 09:08:32 desktop4 kernel: [   76.494293] lo: Disabled Privacy Extensions
Jul 31 09:08:32 desktop4 kernel: [   76.495130] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 31 09:08:43 desktop4 kernel: [   87.252046] eth1: no IPv6 routers present
Jul 31 09:54:05 desktop4 kernel: [ 2805.333740] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 09:54:17 desktop4 kernel: [ 2817.319509] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:14:52 desktop4 kernel: [ 4051.125469] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:15:04 desktop4 kernel: [ 4063.114233] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:16:48 desktop4 kernel: [ 4166.645615] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:16:48 desktop4 kernel: [ 4166.661593] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:35:42 desktop4 kernel: [ 5299.229045] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
Jul 31 10:35:42 desktop4 kernel: [ 5299.239027] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94

```

The same last couple of lines appear in /var/log/syslog and /var/log/messages.

Anyone else have problems with the zd1211rw driver causing freezes, and is there a solution?  Before someone suggests it, I've had problems with ndiswrapper and I really don't want to go that route again.  I guess one solution would be downloading and recompiling the kernel zd1211rw kernel module, and disabling the one provided with Ubuntu.  However, I'm not completely sure how to go about doing this.  Thanks for any help!

---

