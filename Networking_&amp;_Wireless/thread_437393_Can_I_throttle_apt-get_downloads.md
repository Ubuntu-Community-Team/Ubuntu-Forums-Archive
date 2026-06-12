---
title: "Can I throttle apt-get downloads?"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Dr_Snapid on 2007-05-08
Is it possible to only allow apt-get to download at a certain speed? Like maybe limit it to half my bandwidth, so my web browser isnt so crippled?

I have 512K ADSL and I am upgrading dapper to edgy, but the 790Mb  download is tying up my bandwidth making it hard to continue browsing.

I'd also be interested to know if you can do the same with wget...

---

### Post by kidders on 2007-05-10
Hi there,

Applications sometimes have a setting you can tweak to limit their use of network resources. I don't seem to be able to find one for apt either, which is a little surprising, to be honest.

I would be tempted to go for an application non-specific solution to your problem. The trouble is that controlling the speed at which a remote computer sends you something is not trivial, and requires quite a bit of reading & messing about, to get the firewall & traffic shaping rules just right.

---

### Post by spd106 on 2007-05-10
This post on the debian forums might be of interest [http://forums.debian.net/viewtopic.php?t=275&](http://forums.debian.net/viewtopic.php?t=275&)

I must admit that I haven't tried it.

wget can be throttled using the --limit-rate switch, check the man page for details.

---

