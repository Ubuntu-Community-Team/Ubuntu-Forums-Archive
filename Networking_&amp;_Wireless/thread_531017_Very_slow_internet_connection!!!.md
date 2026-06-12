---
title: "Very slow internet connection!!!"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2007-08-21
Hello,

I access my internet over a wireless connection. I'm getting pathetic speeds in UBuntu (2-3kb/sec!!) whereas I'm getting a steady stream of 60kb/sec in windows. What's slowing things down so much in Ubuntu? Please help. Am a noob.

---

### Post by will71110 on 2007-08-21
how close are you to the AP?

---

### Post by Steve1961 on 2007-08-21
What wireless chipset are you using (try lspci -v to find out if you're not sure)

---

### Post by rkakkar on 2007-08-26
> **will71110 said:**
> how close are you to the AP?

I don't think distance is the problem because with the same distance i'm getting a steady stream of 60k/s in windows by 2-3k/sec in ubuntu

---

### Post by rkakkar on 2007-08-27
> **Steve1961 said:**
> What wireless chipset are you using (try lspci -v to find out if you're not sure)

```
01:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: D-Link System Inc DWL-G510 Rev C
        Flags: bus master, slow devsel, latency 32, IRQ 18
        Memory at e0000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

```

I'm willing to be patient with ubuntu, but i need you guys to help me out! :). i've done a fresh install and the only changes made so far is disabling ipv6 in swiftfox.

---

### Post by Steve1961 on 2007-08-27
You have the rt61 chipset.  Have a look at these link to see if they help:

[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

or here:

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

---

### Post by rkakkar on 2007-08-29
> **Steve1961 said:**
> You have the rt61 chipset.  Have a look at these link to see if they help:

[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

or here:

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

works perfectly!! another happy ubuntu user! :guitar:

---

