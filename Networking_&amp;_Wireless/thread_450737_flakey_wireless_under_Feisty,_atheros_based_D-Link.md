---
title: "flakey wireless under Feisty, atheros based D-Link"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by moron on 2007-05-21
Howdy.  I very recently setup a new Feisty Kubuntu based box to replace my aging Gentoo one.  I have the following Atheros based card installed:

03:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1b
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

The kernel in this case is 2.6.20-15-generic #2 SMP x86_64 GNU/Linux.

From a default install I was able to run "iwlist scanning" and see my local router in the list.  I was unable to however get KNetworkManager to successfully authenticate.  Since then,  I have hard coded the details for my connection into /etc/network/interfaces and using " sudo /etc/init.d/networking restart " I can authenticate and get a network connection.

The problem I am having however is that after a seemingly random period of time (anywhere from a minute or two to an hour), the connection dies.  When this occurs, if I try to ping any host (other than localhost of course) I get a network unreachable error.  I do however still see my router if I use iwlist.  I see no obvious errors in messages or with dmesg.  

Being new to the Kubuntu layout, I am not sure where to start to try to get some meaningful error messages.  I am assuming this is an issue with wpa_supplicant or possibly the madwifi network driver but without any obvious errors I am not sure how to proceed here.

I should note that previously under Gentoo this card worked without any issue so unless there is some conflict with the new box I am running this in, this seems either like a software problem or possibly there is some service running which is messing with the network.

Anyway, if anyone has some suggestions on how to get wpa_supplicant to be more verbose with what it is doing would be much appreciated.

Cheers

---

### Post by scrooge_74 on 2007-05-21
I have my own fights myself, I keep using either wifi-radar, network-manager, the buit in network tool or the command line to keep my self online.

For instance network manager sometimes will say I am conected but in fact I am not, I have to manually overwrite the config on /etc/network/interfaces to get it to reset and then get the conection going.  

Still when I get it to work it is pretty good.

---

### Post by spoonernash on 2007-08-08
Moron, the problem you describe is similar to my current problem. Kubuntu with D-Link WNA 2330 using madwifi and wpasupplicant. Random loss of wifi connection. Can't find any clues in logs.

Did you find a resolution?

---

### Post by moron on 2007-08-08
> **spoonernash said:**
> Moron, the problem you describe is similar to my current problem. Kubuntu with D-Link WNA 2330 using madwifi and wpasupplicant. Random loss of wifi connection. Can't find any clues in logs.
Did you find a resolution?

Howdy.  So far no solution though I did notice that the madwifi driver installed with Feisty is ancient (about a year out of date).  I have since installed a deb from Gusty that updates this to something more recent 0.9.3 (I think).  Since doing that the connection seems to be a bit more reliable and restarts more reliably than before though it does still cut off periodically.

Finding the culprit is likely going to require compiling everything from scratch I expect.

Cheers

---

### Post by peterv6 on 2007-09-09
Moron,
I'm having problems with the same card.  I bought it last night, and it took hours to get it to work with Fiesty.  When I logged back in this morning, no connection.  I had to fiddle around with it again, got it going, and restarted to see if the problem would happen again.  (It did.)  I haven't been able to get connected since.  (I knew I should have written down all the steps & settings the first time.)  Any chance you'd mind posting where you got the driver, and the steps needed to install it?  I'm pretty new to this stuff, so the directions would be really helpful.
Thanks,
PETER V.

---

