---
title: "Kernel warning ixgbe"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by howard8 on 2014-08-13
Hi Guys, I'm running this old server with kernel 2.6.27-16-server. For some reason I cannot update my system, and I have to use this new 10G NIC.
After installed the latest ixgbe driver, I got this kernel message running some stress tests.

Call Trace:
<IRQ>  [<ffffffff8045dd4c>] ? skb_release_data+0xc/0xd0
[<ffffffff8045e369>] ? skb_release_all+0xb9/0x100
[<ffffffff8045dc36>] ? __kfree_skb+0x16/0xa0
[<ffffffff8045dcdc>] ? kfree_skb+0x1c/0x40
[<ffffffff80464440>] ? dev_kfree_skb_any+0x50/0x60
[<ffffffffa0227f22>] ? ixgbe_poll+0x122/0x16a0 [ixgbe]
[<ffffffff8046828c>] ? net_rx_action+0x10c/0x250
[<ffffffff80254eac>] ? __do_softirq+0x8c/0x100
[<ffffffff8021417c>] ? call_softirq+0x1c/0x30
<EOI>  [<ffffffff80215875>] ? do_softirq+0x65/0xa0
[<ffffffff80255591>] ? local_bh_enable_ip+0xb1/0xc0
[<ffffffff80504145>] ? _read_unlock_bh+0x15/0x20
[<ffffffffa0363034>] ? fpForward+0x424/0x2a00 [fp]
[<ffffffffa03574e1>] ? fpFlowIdTouch+0x21/0x320 [fp]
..........

Is anyone has an idea about this?

Thank you!

---

### Post by Bashing-om on 2014-08-14
howard8; Hi ! Welcome to the forum.
Real old kernel:
> 
kernel 2.6.27-16-server.
 in and of it's self is not a problem.
What might be the problem is trying to run a GUI on top of that release.
Show us what the situation is, post back the outputs - Between code tags - of terminal commands:
```

lsb_release -a
uname -a
echo $DESKTOP_SESSION

```
as the desktop for release 10.04 is no longer supported, possible that an update to that possible GUI desktop has broken your server.
-at release of 10.04 the desktop had 3 years of support, the server has 5 years-

[INDENT][INDENT]good place to start
[/INDENT][/INDENT]

---

### Post by howard8 on 2014-08-14
> **Bashing-om said:**
> howard8; Hi ! Welcome to the forum.
Real old kernel:
 in and of it's self is not a problem.
What might be the problem is trying to run a GUI on top of that release.
Show us what the situation is, post back the outputs - Between code tags - of terminal commands:
```

lsb_release -a
uname -a
echo $DESKTOP_SESSION

```
as the desktop for release 10.04 is no longer supported, possible that an update to that possible GUI desktop has broken your server.
-at release of 10.04 the desktop had 3 years of support, the server has 5 years-
[INDENT][INDENT]good place to start
[/INDENT]
[/INDENT]


Hi, Thanks for your reply.


```
root@Sub1:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid



root@Sub1:/# uname -a
Linux Sub1 2.6.27-16-server #1 SMP Tue Dec 1 20:06:14 UTC 2009 x86_64 GNU/Linux


```
I think there is no desktop session....

---

### Post by Bashing-om on 2014-08-14
howard8; Yuk !

The bearer of bad news - such is my fate -

The water has gotten deep, you can no longer hold out; as release 8.10 is long long past it's End_Of_Life. And was not a Long_Term_Support release to start with. The supporting software repository is no longer in existence - as you may have known it . That old release has NO support .
The better course of action is to backup your data, and do a clean fresh install of the current release ( 12.04, 14.04).

A version - online upgrade from 8.10 is not even thinkable, way too much has changed in the operating system since those old days of 8.10.
8.10 -> 9.04 -> 9.10 ->10.04 ->12.04 -> 14.04 // The translations between 10.04 and 12.04 are a killer -> it is a whole new world now.

[INDENT][INDENT]it's the truth, the whole truth
[INDENT][INDENT][INDENT][INDENT]and nothing but the truth
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by howard8 on 2014-08-15
Yeah... I understand.. That is what I worried about, but thank you any way.

---

### Post by Bashing-om on 2014-08-15
howard8; Hey ;

Mind you we are behind you all the way.

Burn you a liveDVD and boot to "try ubuntu" as a desktop to verify that your hardware supports the later ubuntu operating system. Then burn that server edition and install.

Bear in mind, any hesitations or concerns or difficulties, we are here to respond.

[INDENT][INDENT][INDENT]a big step forward for 'buntu kind
[/INDENT][/INDENT][/INDENT]

---

