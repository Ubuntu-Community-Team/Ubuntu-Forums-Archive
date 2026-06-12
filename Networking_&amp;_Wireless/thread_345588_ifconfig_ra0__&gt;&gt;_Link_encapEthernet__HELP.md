---
title: "ifconfig ra0  &gt;&gt; Link encap:Ethernet  HELP"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by neilford on 2007-01-24
I have been following thread:

[http://ubuntuforums.org/showthread.php?t=132980&highlight=belkin](http://ubuntuforums.org/showthread.php?t=132980&highlight=belkin)

I think I was doing everything okay, but when I ran ifconfig ra0, I noticed that ifconfig returned that ra0 was on an ethernet when I am trying to set it up wireless. Is it possible that the interfaces file is configuring it as an ethernet? Or is it possible that something in the rt61.dat file is setting it to ethernet? Where could I look for this?
When I run iwlist ra0 scan I see the wireless network id. I just can't assign it.
Also, when I run dmesg, I get a message that ra0 is using old /proc/net/wireless support. Why isn't it using the rt61 driver I installed?
Running lspci shows the board with the RT61 chipset in it
Thanks.

neilford

---

### Post by neilford on 2007-01-24
I could sure use some ideas here. Thanks.

neilford

---

### Post by neilford on 2007-01-26
Can anyone offer some help? Plese...

neilford

---

