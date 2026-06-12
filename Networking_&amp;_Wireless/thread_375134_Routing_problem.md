---
title: "Routing problem"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by George00 on 2007-03-03
Okay, first off, English is not my primary language so please excuse my bad grammar/spelling.
Second, my problem sounds like this:
I have 3 computers; my mainbox runs Ubuntu and has 3 network adapters installed:
It connects to the internet via the eth2 interface.
It also connects to my other 2 boxes via eth0 and eth1.

Now, can someone give me a few hints on how can I configure my internal network and what iptables rules must I use in order to enable Internet access on all 3 boxes using one external IP address?

On WindowsXP I could do that using Internet Connection Sharing and Net Bridge but now I'm kinda clueless. (oh, and I know it would be a lot more easy if I could use a hardware router)

---

### Post by ingo on 2007-03-04
I think you may want to google "basic networking linux" for that one... Or check the tricks & tips section of this forum...

---

### Post by koenn on 2007-03-04
it comes down to this :
[http://ubuntuforums.org/showpost.php?p=2135536&postcount=2](http://ubuntuforums.org/showpost.php?p=2135536&postcount=2)

Note that the the 'output interface' ( -o ) where you MASQUERADE should be the interface connected to the internet - that's eth2 in your example. 

You will also need to confogure your 2 internal networks, the main point is that they get the ip address of your 'linux router' as default gateway. That would be the ip address if the interface they are connected to.

If you search these forums for ICS or Internet Connection Sharing, you'll find quite a few threads dealing with this

---

