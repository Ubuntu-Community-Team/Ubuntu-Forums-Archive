---
title: "Problem with network connection..."
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by rex1825 on 2007-12-26
I have AirLive 2000PCI WAN & noIP PPPoE connection, had problems wiht connection
[http://ubuntuforums.org/showthread.php?t=649606](http://ubuntuforums.org/showthread.php?t=649606)
but I've overcomed it, that's what I taught!

My dsl-provider file is
[I]# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so
nic-wlan0
user "XXXXXXXX"
usepeerdns[/I]

& it happends that connection just sotps, never happend on XP, wonder what for is *#holdoff 20*? Does this kill connection?!?

Does any body have any clue what is going on?

I also have uncompiled drivers for my WAN card, but it works without them, & GG recognizes it, so that should be no problem, or maybe it is a problem?

Any suggestions?

Please, need help, can't do anything without internet!

Thanks in advacne...

---

