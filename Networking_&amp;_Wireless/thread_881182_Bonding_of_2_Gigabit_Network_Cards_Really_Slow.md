---
title: "Bonding of 2 Gigabit Network Cards Really Slow"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by drunkn on 2008-08-05
Hi all

So I followed this guide:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

to bonding my server mobo's two ethernet cards together. I got it successfully working but it is painfully slow. I know bonding 2 1Gigabit network cards does not produce a 2Gigabit connection but rather 2 1Gigabit 'lanes' however the speeds I'm getting while transferring a file are ridiculously slow.

Any quick troubleshooting things I can do? 

Thanks

---

### Post by casevh on 2008-08-06
What kind of switch are you using?

What kind of performance are you trying to acheive?

Typically, a switch will require configuration changes to support a bonded link. This sounds like a switch that doesn't like what you've done.

casevh

---

### Post by drunkn on 2008-08-06
So I think this is a samba issue, I just tried scp'ing something and I got around 40mbps (megabytes) so I think it's all good.

I've tried fooling around with the SO_RCVBUF and SO_SNDBUF but to no avail it's going ridiculously slow...

Any advice?

I'm running a system with a 10k rpm boot drive and a raid 6 8TB array. The boot drive is running around 85mbps reads/writes and the array is doing around 500mbps reads/writes so there's no bottle neck there..

edit: I am using a netgear gs105 switch.

---

### Post by nixgeek on 2008-08-07
So what mode are you setup to use? Also did you set Samba to bind to the bond0 IP address?  That is if you set it to bind to a particular address.

Here is good article on [Linux Bonding]("http://www.linuxfoundation.org/en/Net:Bonding")....

Note: Most standard switches cannot do mode=4 802.3ad Link Aggregate.

---

### Post by drunkn on 2008-08-19
Hi, 

yeah I tried setting the interfaces option in samba and it still is slow. I'm doing mode 0 , round-robin.

Thanks

---

