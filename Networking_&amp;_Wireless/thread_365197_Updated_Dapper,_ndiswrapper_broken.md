---
title: "Updated Dapper, ndiswrapper broken"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Kurdt on 2007-02-19
Hi :)

I update my ubuntu dapper whenever I see the new updates icon pops up, so I let it did his work last friday, today I power on my computer and I notice that my wlan won't work anymore, doing some research I noticed that ndiswrapper module is failing to load with this error:

> $ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Invalid argument

(the file exists)

and in the logs:

> Feb 19 09:30:22 Andy64 loadndisdriver: loadndisdriver: main(638): version 1.8 doesn't match driver version 1.7

I did some research on internet and everything points to "use 1.8 version, that's the version that works" but I do have 1.8:

> $ ndiswrapper -v
utils version: 1.8
driver version:        1.8
vermagic:       2.6.15-28-386 preempt 486 gcc-4.0

So, what might could happen in the last update? I read on /var/log/dpkg that linux-image-2.6.15-28-386 was installed and linux-restricted-modules too. Maybe is there some incompatibility with this new kernel?

Thanks in advance

---

### Post by spd106 on 2007-02-19
Maybe try running **sudo depmod**.

---

### Post by Kurdt on 2007-02-19
Update:

I loaded ubuntu with 2.6.15-27-386 kernel and ndiswrapper **works good** as always did. :confused:

---

### Post by Kurdt on 2007-02-21
anyone  ? please ? any clue?

---

