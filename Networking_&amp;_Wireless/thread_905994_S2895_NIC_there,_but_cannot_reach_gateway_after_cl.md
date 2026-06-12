---
title: "S2895 NIC there, but cannot reach gateway after clone from working system"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by JumpingCOWS on 2008-08-30
I got an issue, and I'm out of tissues.

A system with Tyan S2895 mobo today had its drive go wack today.

Hooking it up to another system.. A Tyan S2881 I was able to mount the drive and attempt to recover it. I got to a certain point where I just could not get it to boot, so I gave up on it. 

I didn't have time to get everything setup again. So I decided to clone that exact same S2881 drive onto another drive and install it into the S2895. They are almost identical mobos except one has PCIX the other PCIExpress. 

Everything appeared to work fine, except for one thing. I cannot get the NICs to work. I have searched for literally 5 hours to find a solution to this. 

lspci shows the devices
lsmod shows forcedeth

network config like I said is the same as a working system.. so whats the deal? What am I missing?

Since the drive is cloned, the network settings are identical to the working system, except of course for changing it to its own IP. I cannot get it to talk to the gateway though.

No DHCP, all static.

What needs to be done to get the nics working.

It's running Ubuntu 7.04. 

I will gladly send $50 to the person who gives me the answer that gets this working.

I got a KVM on the system and the old drive mounted as a second drive if there is anything I need from that.

Thanks

---

### Post by JumpingCOWS on 2008-08-31
Well.. issue solved.

If anybody is stuck on this like I was.. go into /etc/iftab and see if the MAC address from the previous server is in there.. once I removed them and just had:

eth0
eth1

Everything came up great.

Whew!

---

