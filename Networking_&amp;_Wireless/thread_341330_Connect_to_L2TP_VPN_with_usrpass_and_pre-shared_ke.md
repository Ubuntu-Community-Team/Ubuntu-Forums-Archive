---
title: "Connect to L2TP VPN with usr/pass and pre-shared key?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by tomane on 2007-01-18
Hi,
I want to connect to a VPN.
These are the data that I have:
server ip
username/pass
pre-shared key

I use these data on windows XP and it connects ok.
The connection information show the following:
connection type (or something like that): L2TP
server type: PPP
authentication: MD5 CHAP
Encryption: IPSec, ESP 3DES

I've been searching for a way to connect to that server in (k)ubuntu but so far didn't have any results. Does anyone have pointers to configure this connection? This is really important, as I'm accessing an svn repo through this VPN but if I can't make it work I'll have to shift to windows :s

Cheers,
--to.

---

### Post by tomane on 2007-01-19
SO, hasn't anyone acomplished this yet?
I've been searching and reading stuff for two days and this is getting rather frustrating.
This is an issue that really should be looked at, as a vpn is essential for many people's work and presently is it rather unusable :(

--to

---

### Post by tomane on 2007-01-23
I found this guide and it was the only resource that made the trick for me.
check out [http://www.jacco2.dds.nl/networking/linux-l2tp.html](http://www.jacco2.dds.nl/networking/linux-l2tp.html) if you need to set up a simillar vpn connection.
Kvpnc now supports l2tp over ipsec but it is still under development. You can also check it's homepage, [http://home.gna.org/kvpnc/en/index.html](http://home.gna.org/kvpnc/en/index.html) and download the .deb (there are debs for dapper and etchy [edgy?] ).
I haven't tried it yet because I have the vpn working with Jacco's guide and don't want to blow it up now (just in case hehe) but if anyone tries it meantime, please post. By the end of the week, I'll be able to test it in feisty and see if works.

**EDIT:** kvpnc is 0.8.7-1 in feisty repositories, acording to packages.ubuntu.com, which means that fiesty will have improved support for more vpn setups. \\:D/
Cheers,
--to

---

### Post by andyeddy525 on 2007-01-25
Hey man, thanks for your post.  I've been trying to get this same type of connection to work...  I'm going to reboot into ubuntu and give it a whirl.

Thanks again
ed

---

