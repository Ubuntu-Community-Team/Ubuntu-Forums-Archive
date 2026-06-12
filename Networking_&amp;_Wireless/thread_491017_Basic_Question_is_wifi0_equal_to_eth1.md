---
title: "Basic Question: is wifi0 equal to eth1?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by marc.bonet on 2007-07-03
Hello guys,

I just installed ubuntu the last Saturday night on my Thinkpad t41.  Everything was easy and smooth. Wireless is working ok and was configured via the Network Settings applet. However, I got some questions:

1. Why I see 2 wireless interfaces wifi0 and eth1 (eht0 is the wired interface)?
2. I know the are the same (ifconfig tells me that -same mac address-)... which one should I configure in the networking applet (right now both are configured equal -and wireless is ok-)
3. How can I hide (and which should I) one of them. I found this two interfaces kind of confusing.

Some further comments:

I came from debian... I was a debian user from about 2 years from now. In debian a managed to set up wireless ok, however it was a really painful process (more than two days of fighting with ifconfig, iwconfig, ifdown, ifup, wevent, wspy, etc.). So, I just wanted to say that ubuntu is really nice and straightforward... same applies to VPN... very easy, just amazing. Please check out the following list.

Easy things in ubuntu but very painfully in debian:
1. wireless support
2. sound support (debian was confusing... oss, alsa, oss-alsa-pluging, asd, etc.) 
3. high memory support (in debian had to recompile the kernel in order to see more than 1 MB)
4. vpn support (in debian had  to recompile the kernel in order to use pptp)
5. Hardware things (power management, screen bright meter, sound meter, suspend, etc.)

As you guys can see I'm just loving ubuntu!
The only thing... this two -but same one- wireless interfaces.
Any help or comment is very welcome.
Thanks in advance,
-marc

---

### Post by ubuntuuser on 2007-07-03
I guess your laptop has an Atheros chipset? If so, then I know the answer. 

Use eth1. wifi0 is a base device used by the driver, while eth1 is the actual interface you have to use (called VAP in the driver).

Have a look [here,]("http://madwifi.org/wiki/UserDocs/UsersGuide#a1.2Usingwlanconfig") it's explained a little.

---

### Post by marc.bonet on 2007-07-03
Hello and thanks for your reply.

I saw the information provided by you and I believe it must be the explanation.
However, I don't know exactly which one is my chipset. Below is the lspci -v output filtered only with the network controllers.

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
        Subsystem: IBM PRO/1000 MT Mobile Connection
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0220000 (32-bit, non-prefetchable) [size=128K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 8400 [size=64]
        [virtual] Expansion ROM at c0240000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
        Subsystem: AIRONET Wireless Communications Unknown device 5000
        Flags: bus master, fast devsel, latency 64, IRQ 11
        I/O ports at 8000 [size=256]
        Memory at c0210000 (32-bit, non-prefetchable) [size=16K]
        Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
        [virtual] Expansion ROM at c0800000 [disabled] [size=2M]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data

I assume that my chipset is AIRONET Wireless Communications Cisco Aironet Wireless 802.11b. Is this ok?

Well, let's say that wifi0 is the underlaying network device for eth1, is there any way to prevent wifi0 being showed in the interfaces list on the network settings screen?

Thanks in advance and regards,
-marc

---

### Post by ubuntuuser on 2007-07-05
I know of no way to hide an adapter without deactivating it, and doing so would render your wireless useless, which probably isn't what you want ;)

I only did a very quick search, so I can't say anything definite, but it looks like the Cisco Aironet is indeed the chipset. It doesn't matter, what I said is most likely still correct, I just didn't know that any other driver also uses virtual APs. Btw, the Intel thing is your LAN controller.

---

### Post by marc.bonet on 2007-07-05
Well ubuntuuser,

I think I can live with this wifi0 in the network manager. The important thing is that now I know what it is. Thank you very much and best regards,
-marc

---

