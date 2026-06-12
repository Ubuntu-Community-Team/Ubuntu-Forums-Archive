---
title: "wired network problem"
date: 2019-04-28
forum: Networking &amp; Wireless
---

### Post by jgw on 2019-04-28
I have a wired network that just stopped working.  I have no clue.  I have, however, done a bunch of tests which can be found here:
[https://pastebin.com/ef3PvqB4](https://pastebin.com/ef3PvqB4)

I have also tried to reboot to see if that could help - it didn't.

Thank you..................

---

### Post by him610 on 2019-04-28
Please show, between code tags, results of 
```

inxi -N
ip add

```

---

### Post by jgw on 2019-04-29
Thank you for the reply.  Here are the results:
greg@movies:~$ inxi -N
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           Card-2: Ralink MT7601U Wireless Adapter
greg@movies:~$ ip add
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 40:8d:5c:4d:8d:8e brd ff:ff:ff:ff:ff:ff
3: wlx008736326fa1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:87:36:32:6f:a1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.58/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx008736326fa1
       valid_lft 86256sec preferred_lft 86256sec
    inet6 fe80::8d93:d7fc:af2d:e2d8/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
12: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.90.10.6 peer 10.90.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::c1a:1ea3:431e:7576/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever

I should also add that this is not connected directly to the router.  Instead its connected to a d-link powerline av2-2000 gigabit kit.  Its been working flawlessly up to now.

---

### Post by him610 on 2019-04-29
I have an older model of a powerline adapter that I sometimes use; not very fast, but it works. Recheck all of your of your cable connections, and make sure your two powerline adapters are talking to each other. Are the indicator LEDs displaying the correct color and sequence?  
Can you ping the router?

---

### Post by jgw on 2019-04-30
Thank you for the replies.

I talked to d-link about their stuff yesterday morning, tried everything they suggested - no cigar.   I disconnected, re-connected, reset both, swapped out all the cables, etc. all to no avail.  Then I posted this.  This morning, I checked it again, having done absolutely nothing to fix anything and hoping against hope somebody would have a solution.   Anyway, this morning I checked it again and its working again.  This remains a mystery.  Anybody who thinks computers are all science, and not magic, would be wrong.  I have been building and programming them for 30 years and always believed that one.

Anyway, I have also noticed others have had problems that seemed to have fixed themselves over the years.   I actually think its getting better!  Just goes to show - just not sure what.

I am going to mark this as solved - too bad there is not another category called "mystically solved", or "magically solved"  (either would be fine with me!)

Thanks again.....................

---

### Post by him610 on 2019-04-30
> This remains a mystery.
Yes, occasionally that happens. Sometimes the best action is no action, just patience. Doing what you did, if anything, you eliminated a lot of items that may have contributed to your issue. Consider it a learning experience.

---

