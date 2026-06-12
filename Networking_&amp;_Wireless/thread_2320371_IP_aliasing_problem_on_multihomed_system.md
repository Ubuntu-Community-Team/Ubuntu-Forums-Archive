---
title: "IP aliasing problem on multihomed system"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by gtripathi on 2016-04-13
Hi,

I have a multihomed server (Box1) running Ubuntu 12.04 with two ethernet ports (eth2 and eth3) connected to the same subnet. I create an IP alias using

[B]ip addr add AA.BB.CC.DD /28 dev eth2:0
[/B] 
on interface eth2. The IP address AA.BB.CC.DD is also on the same subnet. Running '**ip addr'** displays AA.BB.CC.D as an additional IP along with the original IP address on eth2. Next, I sendgratuitous arp to publicise the new IP address using

**arping -bA -c 1 -I eth2 AA.BB.CC.DD**

On a different box (Box2) running Ubuntu 12.04 and on the same subnet,** "arp -n"** shows the correct association between IP address AA.BB.CC.DD and MAC address of eth2. But from this box I can't ping AA.BB.CC.DD. So, I run 

**arp -d AA.BB.CC.DD**

which removes the arp entry from the cache on Box2 and ping again. The pings then succeed and get a response. But looking at the arp cache now on Box2, using "**arp -n**", I see the MAC address of eth3 (vs eth2) of Box1 associated with AA.BB.CC.DD. If I again send a gratuitous arp with eth2 from Box1, which restores MAC address of eth2 in the arp cache of Box2, the pings stop working again. It seems the IP alias is getting done on eth3 rather than on eth2 on Box1, even though "**ip addr**" shows it being assigned to the correct interface eth2.

I'll appreciate if someone can explain what is happening here and how to correct this problem.

Thanks.

---

### Post by The Cog on 2016-04-13
It might be reverse path filtering dropping packets that arrive on an interface other than the one that says should be used to reach the source network.
Try these two commands to temporarily disable reverse path filtering:
```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/default/rp_filter'
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter'
```

If this works, the configuration can be made permanent by editing the appropriate lines in /etc/sysctl.conf.

---

### Post by gtripathi on 2016-04-13
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/default/rp_filter'
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter'

The above didn't work. I'd like to add that the problem is intermittent.

---

### Post by The Cog on 2016-04-13
That's a shame. I had hopes there. All I can think of is to trace the packets in and out with tcpdump. Since you need to trace two interfaces, you probably need to run two trace commands concurrently in two different consoles:
sudo tcpdump -np -i eth2
sudo tcpdump -np -i eth3

---

### Post by SeijiSensei on 2016-04-13
Connecting two interfaces to a subnet can cause problems.  Why do you need to do that?  What happens if you bring down eth3 and alias eth2?

---

### Post by gtripathi on 2016-04-14
It appears to work if in addition to doing it on 'default' and 'all', I disable RP filtering on the interfaces eth2 and eth3 as well on Box1. I'll test it out few more times to verify if this really is the solution, because even earlier the problem was intermittent. 

Thanks for your help.

---

### Post by gtripathi on 2016-04-14
Bringing down eth3 causes the problem to go away, but then its not a multihomed system anymore. I'm developing something that needs multiple interfaces and currently I have only one subnet to connect with. In real use, the interfaces will be connected to different subnets. Anyway, disabling reverse path filtering on all interfaces seems to work. Thanks

---

### Post by SeijiSensei on 2016-04-14
If you have another PC available, connect that to eth3 and place them both in another subnet.  I bet you'd have no problems then regardless of how reverse path filtering is configured.

---

