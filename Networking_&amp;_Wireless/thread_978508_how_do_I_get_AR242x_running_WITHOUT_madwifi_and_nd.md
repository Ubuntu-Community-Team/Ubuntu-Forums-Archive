---
title: "how do I get AR242x running WITHOUT madwifi and ndiswrapper"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by porchrat on 2008-11-11
Hi all

Just installed 8.10 and am relatively unimpressed so far.  Seems pretty similar to 8.04.  I had read that the new 2.6.27 kernel had solved the MP_BIOS bug, unforunately I see it didn't.  Oh well no SMP for me.

I also see that it doesn't seem to support the AR242x wireless module out of the box, but I have read things that hint that it does support it without the need for madwifi or ndiswrapper.  Is this true and if so how is it acheived and is it reliable?

I'm happy to install madwifi again (worked fine in 8.04), but if I do I dont want to have to reinstall it for every kernel.  I seem to recall a new package that stops you needing to do a "make clean" "make install" everytime you introduce a new kernel.

Any help (or referral to a guide) would be much appreciated.

---

### Post by porchrat on 2008-11-11
Decided I may as well include the output of lshw for you.

```
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:c3:4b:a6:3c:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

As you can see the bloody thing is UNCLAIMED.  Does 8.10 not come with a driver capable of running AR242x out of the box?  What about this ath5x thing I've heard about?

---

### Post by porchrat on 2008-11-11
Nevermind I went with the compat-wireles (basically madwifi) method.  It isn't perfect, but fine for now.  Hopefully I will find some method later that allows me to update the kernel without needing to redo the wireless as it is a little annoying.

At least for now I'm connected.  If anyone has any suggestions please feel free to post here.

---

