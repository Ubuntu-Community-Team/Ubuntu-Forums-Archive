---
title: "Netstat or route commands - how to see the WHOLE network path"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by vperaino on 2014-08-01
So in my office we've got multiple tiers of network equipment to get connectivity to a few different suites. 

Right now I'm going through a wireless router which is being served by a large switch from upstairs. 

However, if I run the **route -n** command, I only see the IP of the switch, and not the wireless router which I am directly connected to. 

Is there any way to display the addresses of ALL the devices I'm connected to locally?

---

### Post by steeldriver on 2014-08-01
Have you tried tracepath (or the older traceroute)?

```

tracepath -b *some.rem.ote.add.ress*

```

```

traceroute *some.rem.ote.add.ress*

```

---

### Post by vperaino on 2014-08-01
Tracepath only identifies my local system and external routes:

> 
me@mybox ~ $ tracepath -b [www.google.com]("http://www.google.com")
 1: mybox.local (192.168.2.218)                        0.185ms pmtu 1500
 1:  23-24-232-238-static.hfc.comcastbusiness.net (23.24.232.238)   2.582ms 
 1:  23-24-232-238-static.hfc.comcastbusiness.net (23.24.232.238)   2.307ms 
 2:  73.193.141.1 (73.193.141.1)                          38.948ms 
 3:  xe-11-1-0-32767-sur02.blairblvd.tn.nash.comcast.net (68.86.149.141)  16.099ms asymm  4 
 4:  xe-5-0-7-0-ar01.goodslettvll.tn.nash.comcast.net (68.86.176.37)  20.007ms 
 5:  he-5-5-0-0-cr01.56marietta.ga.ibone.comcast.net (68.86.90.101)  22.109ms 
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply


---

### Post by ian-weisser on 2014-08-01
The 'arp' command will tell you what your system sees.
Of course, your system may not see everything...or see it accurately.

---

### Post by vperaino on 2014-08-01
Arp shows the main switch as well as our reverse SSH server. No luck!

---

### Post by ian-weisser on 2014-08-01
I don't quite see how your system can be connected to another machine on the LAN and have 'arp' *not *see it. Seems like your machine thinks it is connected only to those two machines, and all other connections pass through one or both of those.

Are you sure your wireless access point isn't acting like a (dumb, non-routing) switch? The only way to see that would be wandering through the interface ifconfigs and iwconfigs.

---

### Post by SeijiSensei on 2014-08-01
> 1: mybox.local (192.168.2.218) 0.185ms pmtu 1500
1: 23-24-232-238-static.hfc.comcastbusiness.net (23.24.232.238) 2.582ms


It looks to me like your router is sending everything out over the Internet.  Shouldn't it be forwarding packets to an upstream router in your organization?

---

