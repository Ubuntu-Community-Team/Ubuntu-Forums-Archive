---
title: "Possible to share internet w/ more than one system?"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by AVT- on 2008-06-13
I can't seem to find any information anywhere, so I'd appreciate if someone would point me in the right direction.

What I'm looking to setup:

..................................wifi (wlan0)
....................................^
Internet (eth0) --> Linux --> Windows (eth1)
....................................v 
.................................voip box (eth2)

I also need to limit the amount of bandwidth per connection. Someone suggested firestarter, however, I can't seem to get it to work, since it just errors (eth1/eth2 not ready)

Is there some kind of GUI, maybe similar to the windows network sharing wizard, to configure this?

Also, due to problems with network monitor, it's been removed from the system. Is there any other tool for configuring a wireless network - for other computers to connect?

---

### Post by madjr on 2008-06-13
get a **switch**

i share my internet with zero configuration

---

### Post by superprash2003 on 2008-06-14
read this.. Internet Connection Sharing [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by AVT- on 2008-06-14
> **madjr said:**
> get a **switch**

i share my internet with zero configuration

I have one. This is intended to replace that, since I'd like a little bit more control over the connection.

> read this.. Internet Connection Sharing [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

I'll take a look. Thanks.

---

### Post by AVT- on 2008-06-14
After setting everything up as stated on that page, I can't connect to the internet on that system anymore.

edit: It's iptables. Purge, and can connect fine now.

edit2: Reset iptables to default settings, and linux connect fine now. However, only one of the two machines can connect to the internet.

edit3: Two NIC's = two subnets. Working now! Thankyou!

---

