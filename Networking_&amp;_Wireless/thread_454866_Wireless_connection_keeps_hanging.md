---
title: "Wireless connection keeps hanging"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by mathenge on 2007-05-25
I gave up the fight with my built-in wireless NIC and bought a PC-Card NIC that's supported. Now, Ubuntu recognizes it at boot time. I had to blacklist the built-in one so that Madwifi wouldn't try to load it as well. I found that after a few minutes of "inactivity" the connection would drop. Checking my routing table, I found that my WIRED connection may have been competing with the wireless one. So, what I've done is disable (using Network Manager) the wired connection. The wireless connection seems to be holding steady.

The routing table looks like this now:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.103.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     *               255.255.255.0   U     0      0        0 ath0
172.16.95.0     *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 ath0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

The wired connection is eth0 and it's not listed any more. Don't worry about the vmnet entries... that's my vmware stuff.

I use this laptop at work, where we only have a wired connection, so at work, I have to enable the WIRED connection. It's a hassle, but not unbearable since it's done only once a day.

I've noticed that there are SO many posts regarding dropped connections. I suggest checking the routing table (just type "route") and see what the default route is pointing to. It should be pointing to your wireless NIC.

Cheers!

Andrew.

---

### Post by dardack on 2007-06-08
Just wanna say thanks for posting this.  Dont' know if it will fix my issue (at work) but i'm willing to try anything.  My connection just drops in and out all the time, and I've been all over these forums trying to find a fix.  Right now at work compiling a list of things to try.  Just saying thanks for the info.

---

